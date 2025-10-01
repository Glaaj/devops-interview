# First stage: build the application
FROM gradle:9.1.0-jdk21 AS build
WORKDIR /app
COPY . .
RUN chmod +x gradlew
RUN ./gradlew clean build --no-daemon --stacktrace

# Second stage: run the application
FROM eclipse-temurin:21.0.2_13-jdk-jammy
WORKDIR /app
COPY --from=build /app/build/libs/helloworld.jar helloworld.jar
EXPOSE 8080
CMD ["java", "-jar", "helloworld.jar"]