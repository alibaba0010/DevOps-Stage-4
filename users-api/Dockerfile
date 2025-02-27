# Use Maven with OpenJDK 8 as the base image for building
FROM maven:3.8.4-openjdk-8 AS build

# Set the working directory inside the container to /app
WORKDIR /app

# Copy the pom.xml file to the working directory
COPY pom.xml .

# Download all dependencies to be available offline
RUN mvn dependency:go-offline

# Copy the source code to the working directory
COPY src ./src

# Build the project and package it into a JAR file, skipping tests
RUN mvn clean package -DskipTests

# Use a slim version of OpenJDK 8 as the base image for running the application
FROM openjdk:8-jre-alpine

# Set the working directory inside the container to /usr/src/app
WORKDIR /usr/src/app

# Copy the JAR file from the build stage
COPY --from=build /app/target/users-api-0.0.1-SNAPSHOT.jar ./users-api.jar

# Expose application port
EXPOSE 8083

# Run application
CMD ["java", "-jar", "/usr/src/app/users-api.jar"]