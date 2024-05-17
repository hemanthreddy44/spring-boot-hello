# Use the official OpenJDK 11 image as the base image
FROM openjdk:11-jdk

# Copy the jar file to the container
COPY target/*.jar app.jar

# Expose port 8080
EXPOSE 8080

# Start the application
ENTRYPOINT ["java","-jar","/app.jar"]