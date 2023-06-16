FROM openjdk:11-oracle
VOLUME /tmp
COPY --chown=node:node target/*.jar app.jar
ENTRYPOINT ["java", "-jar","/app.jar", "--spring.profiles.active=docker"]
