# -------- Stage 1: Build --------
FROM maven:3.9.6-eclipse-temurin-17 as builder

WORKDIR /app

# Copy Maven files first for better layer caching
COPY pom.xml .
COPY src ./src


# -------- Stage 2: Run --------
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Copy the generated jar from Stage 1
COPY --from=builder /app/target/*.jar app.jar

# Expose default Spring Boot port
EXPOSE 8000

# Run the Spring Boot app
ENTRYPOINT ["java", "-jar", "app.jar"]
