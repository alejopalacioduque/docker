### BUILD image
FROM maven:3-jdk-11 as builder
# create app folder for sources
RUN mkdir -p /build
# Define the work dir
WORKDIR /build
# Copy the pom file to build path
COPY pom.xml /build
#Copy source code
COPY src /build/src
# Build application
RUN mvn package


FROM openjdk:11-slim as runtime
#Set app home folder
ENV APP_HOME /app
#Create base app folder
RUN mkdir $APP_HOME
WORKDIR $APP_HOME
#Copy executable jar file from the builder image
COPY --from=builder /build/target/*.jar app.jar
# Define the command to run the app
ENTRYPOINT ["java","-jar","/app/app.jar"]