# Stage 1: Build the JAR using Maven
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn -f /app/vic/pom.xml clean package -DskipTests

# Stage 2: Run the Spring Boot app
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/vic/target/*.jar app.jar
EXPOSE 7000
ENTRYPOINT ["java", "-jar", "app.jar"]
