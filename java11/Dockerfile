FROM adoptopenjdk:11-jre-hotspot
RUN mkdir /opt/app
COPY app.jar /opt/app
CMD ["java", "-jar", "/opt/app/app.jar"]