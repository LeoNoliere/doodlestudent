FROM maven:3.9.6-eclipse-temurin-17-alpine AS build

WORKDIR /doodlestudent/back

COPY . /doodlestudent/back

RUN mvn dependency:copy-dependencies

RUN mvn -N io.takari:maven:wrapper -Dmaven=3.9.6

RUN mvn clean package -Dquarkus.package.type=uber-jar

FROM eclipse-temurin:17-jre-alpine

COPY --from=build /doodlestudent/back/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar /usr/local/lib/demo.jar

CMD java -jar /usr/local/lib/demo.jar
