FROM maven:3.8-openjdk-8 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

FROM openjdk:8-jdk-alpine

LABEL maintainer="bastien"

WORKDIR /app

COPY --from=builder /app/target/*.jar /app/app.jar

EXPOSE 8448

CMD ["java", "-jar", "app.jar"]
