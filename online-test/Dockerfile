FROM ubuntu:latest AS build

# Update package lists
RUN apt-get update

# Install Maven
RUN apt-get install maven -y

# Copy project source code
COPY .. .

# Build the project using Maven
RUN mvn package

# Create a slim base image for the final container
FROM OpenJDK:17-slim-buster

# Expose port 8080
EXPOSE 8080

# Copy the built JAR file from the build stage
COPY build/target/online-test-1.0.0.jar app.jar

# Run the application using Java
ENTRYPOINT ["java", "-jar", "app.jar"]
