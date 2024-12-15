# Use a base image with Java 17 for the build stage
FROM eclipse-temurin:17-jdk as builder

# Set working directory
WORKDIR /app

# Copy Gradle wrapper and project files
COPY gradlew ./
COPY gradle ./gradle
COPY build.gradle ./
COPY settings.gradle ./
COPY src ./src

# Ensure Gradle wrapper is executable
RUN chmod +x ./gradlew

# Build the application with the bootJar task
RUN ./gradlew bootJar --no-daemon

# Runtime stage
FROM eclipse-temurin:17-jre

# Set working directory
WORKDIR /app

# Copy the jar file from the build stage
COPY --from=builder /app/build/libs/apis*.jar app.jar

# Expose the port your Spring Boot app listens on
EXPOSE 8080

# Set environment variables for Spring Boot
ENV SPRING_APPLICATION_NAME=apis

# Run the Spring Boot application
ENTRYPOINT ["java", "-jar", "app.jar"]
