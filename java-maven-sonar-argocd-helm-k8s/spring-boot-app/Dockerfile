# You can change this base image to anything else
# But make sure to use the correct version of Java
# Use an official Maven image with JDK 17
FROM maven:3.9.6-eclipse-temurin-17

# Set working directory
WORKDIR /app

# Copy source code
COPY . .

# Package the app using Maven
RUN mvn clean package -DskipTests

# Use a lightweight JDK 17 base image to run the app
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /opt/app

# Copy the jar from the previous build stage
COPY --from=0 /app/target/spring-boot-web.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]


