FROM maven

COPY src src
COPY pom.xml pom.xml

RUN mvn clean package

CMD mvn gatling:test
