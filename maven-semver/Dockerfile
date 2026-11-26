FROM eclipse-temurin:25-jre-noble@sha256:f3dd0838e69b881cc382237d5901e74ae3705b1056ad964b2e0e523b174fef99

WORKDIR /app
ARG JAR_FILE=target/maven-semver-1.0.0.jar
COPY --chmod=0444 ${JAR_FILE} /app/maven-semver.jar

USER 10001:10001
ENTRYPOINT ["java", "-jar", "/app/maven-semver.jar"]
