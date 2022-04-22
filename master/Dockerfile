# syntax=docker/dockerfile:1

##
## Build
##
FROM maven:3.6.1-jdk-8-alpine AS MAVEN_BUILD

WORKDIR /app

COPY ./ ./
# RUN mvn clean package 

# the second stage of our build will use open jdk 8 on alpine 3.9
FROM openjdk:8-jre-alpine3.9

# copy only the artifacts we need from the first stage and discard the rest
#COPY --from=MAVEN_BUILD /*/target/spring-boot-helloworld-0.0.1-SNAPSHOT /spring-boot-helloworld-0.0.1-SNAPSHOT.jar
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} application.jar



##
## Deploy
##



EXPOSE 8080

USER root

ENTRYPOINT ["java","-jar","/application.jar"]
