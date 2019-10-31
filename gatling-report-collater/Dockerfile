FROM registry.access.redhat.com/ubi7/ubi

ARG GATLING_VERSION=3.3.0
ENV GATLING_VERSION $GATLING_VERSION
ENV APP_ROOT=/opt/app-root


### Containers should NOT run as root as a good practice

WORKDIR ${APP_ROOT}

RUN cd ${APP_ROOT} && yum install -y wget zip unzip java-1.8.0-openjdk-headless.x86_64 \
  && wget https://repo1.maven.org/maven2/io/gatling/highcharts/gatling-charts-highcharts-bundle/$GATLING_VERSION/gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip \
  && unzip gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip

RUN chgrp -R 0 ${APP_ROOT} && \
      chmod -R g=u ${APP_ROOT} /etc/passwd
VOLUME ${APP_ROOT}
USER 10001
CMD find /opt/gatling/$GATLING_REPORT_DIR  -name "*.log" | sed 's,\(.*\)\/\(.*\.log\),mv & \1_\2,' | bash; ${APP_ROOT}/gatling-charts-highcharts-bundle-$GATLING_VERSION/bin/gatling.sh -ro /opt/gatling/$GATLING_REPORT_DIR
