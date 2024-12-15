# Build Stage
FROM eclipse-temurin:17-jdk as builder
WORKDIR /app
COPY build.gradle .
COPY settings.gradle .
COPY gradlew .
COPY gradle ./gradle
COPY src ./src
RUN chmod +x gradlew
RUN ./gradlew bootJar --no-daemon

# Runtime Stage
FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=builder /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
