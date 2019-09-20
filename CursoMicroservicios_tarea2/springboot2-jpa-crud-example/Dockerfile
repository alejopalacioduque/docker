### BUILD image
FROM maven:3-jdk-11 as builder
# create app folder for sources
RUN mkdir -p /build
WORKDIR /build
COPY pom.xml /build
#Copy source code
COPY src /build/src
# Build application
RUN mvn package


FROM openjdk:11-slim as runtime
EXPOSE 8080
#Set app home folder
ENV APP_HOME /app
#Create base app folder
RUN mkdir $APP_HOME
WORKDIR $APP_HOME
#Copy executable jar file from the builder image
COPY --from=builder /build/target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app/app.jar"]