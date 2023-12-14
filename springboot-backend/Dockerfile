# Use an official OpenJDK 11 image as the build image
FROM openjdk:11 AS BUILD_IMAGE

# Set the working directory to /app
WORKDIR /app

# Copy the local project directory to the image
COPY . /app

# Install Maven
RUN apt update && apt install maven -y

# Run Maven install
RUN mvn install

# Continue with the rest of your Dockerfile
FROM tomcat:9-jre11

# Remove the default Tomcat webapps
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy the built WAR file from the build image to the Tomcat webapps directory
COPY --from=BUILD_IMAGE /app/target/springapp-v1.war /usr/local/tomcat/webapps/ROOT.war

# Expose port 8080
EXPOSE 8080

# Start Tomcat
CMD ["catalina.sh", "run"]
