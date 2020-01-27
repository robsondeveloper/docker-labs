FROM openjdk:8-jdk-alpine
RUN mkdir -p /usr/src/myapp
COPY demo.jar /usr/src/myapp
WORKDIR /usr/src/myapp
CMD ["java", "-jar", "demo.jar"]