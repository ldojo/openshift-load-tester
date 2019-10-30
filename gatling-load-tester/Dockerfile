FROM maven
WORKDIR /opt/app-root
COPY src src
COPY pom.xml pom.xml

RUN mvn clean package
VOLUME /opt/gatling/
CMD mvn gatling:test; mkdir /opt/gatling/$GATLING_LOG_DIR ; find target/gatling -name "*.log" -exec cp {} /opt/gatling/$GATLING_LOG_DIR/  \;
