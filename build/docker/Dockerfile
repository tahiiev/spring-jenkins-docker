FROM openjdk:11
VOLUME /tmp
#ARG JAR_FILE
ADD ../../../../build/libs/spring-boot-jenkins-docker-1.0.jar app.jar
ENTRYPOINT ["java","-jar", "app.jar"]
