FROM openjdk:17-jdk-slim AS build

# Set the working directory in the container
WORKDIR /app
# Copy the Spring Boot jar from the target directory into the container

COPY target/apis.jar /app/apis.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "/app/apis"]