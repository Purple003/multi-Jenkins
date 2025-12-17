# Étape 1 : Build avec Maven
FROM maven:3.8.4-eclipse-temurin-17 AS builder
WORKDIR /app
COPY ./pom.xml ./
COPY ./src ./src
RUN mvn -B -U clean package -Dmaven.test.skip=true

# Étape 2 : Image finale avec JDK
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar car-service.jar
ENTRYPOINT ["java", "-jar", "/app/car-service.jar"]
