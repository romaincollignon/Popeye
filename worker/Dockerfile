FROM maven:3.5-jdk-8-alpine AS builder
COPY . /src/
WORKDIR /src/
RUN mvn package
RUN mvn dependency:resolve
FROM openjdk:8-jre-alpine
COPY --from=builder /src/target/ /src/target/
WORKDIR /src/target/
CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]
