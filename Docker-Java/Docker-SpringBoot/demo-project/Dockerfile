FROM openjdk:17-jdk-slim
EXPOSE 8080
ENV CODE_DIR /usr/src/app
COPY target/*.jar $CODE_DIR/app.jar
WORKDIR $CODE_DIR
CMD ["java", "-jar", "app.jar"]
