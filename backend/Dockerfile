# Stage 1: Build Stage
FROM maven:3.8.7-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Runtime Stage
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/app.jar app.jar

# Expose port 8080 for the backend
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
