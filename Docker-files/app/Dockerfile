# Use an official OpenJDK 11 image as the build image
FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone -b master https://github.com/Redtius/Angular-Spring-Deployment.git
RUN cd Angular-Spring-Deployment/springboot-backend && git checkout master && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /app/target/springapp-v1.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
