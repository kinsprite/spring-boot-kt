FROM openjdk:8-jdk-alpine AS build

RUN mkdir /work
COPY . /work
WORKDIR /work
RUN /work/gradlew build


FROM openjdk:8-jre-slim

EXPOSE 8080

RUN mkdir /app
COPY --from=build /work/build/libs/*.jar /app/spring-boot-application.jar

ENTRYPOINT ["java", "-jar", "/app/spring-boot-application.jar"]
