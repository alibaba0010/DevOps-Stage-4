FROM maven:3.8-openjdk-11
WORKDIR /app
COPY . .
RUN mvn clean install -DskipTests
EXPOSE 8083
CMD ["java", "-jar", "target/users-api-0.0.1-SNAPSHOT.jar"]