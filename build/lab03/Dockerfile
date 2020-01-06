####
# This Dockerfile is used in order to build a container that runs the Quarkus application in native (no JVM) mode
####

FROM maven:3.6.3-jdk-8 as mavencache
ENV MAVEN_OPTS=-Dmaven.repo.local=/mvn
COPY pom.xml /app/
WORKDIR /app
RUN mvn test-compile dependency:resolve dependency:resolve-plugins

FROM oracle/graalvm-ce:19.2.1 AS native-image
ENV MAVEN_OPTS=-Dmaven.repo.local=/mvn
COPY --from=mavencache /mvn/ /mvn/
COPY . /app
WORKDIR /app
# Build native image
ENV GRAALVM_HOME=/usr
RUN gu install native-image && \
    ./mvnw package -Pnative -Dmaven.test.skip=true && \
    # Prepare everything for final image
    mkdir -p /dist && \
    cp /app/target/*-runner /dist/application && \
    chmod -R 775 /dist

# FROM centos
# FROM alpine
# FROM gcr.io/distroless/base
FROM scratch
WORKDIR /work/
COPY --from=native-image /dist /work
EXPOSE 8080
# USER 1000
CMD ["./application", "-Dquarkus.http.host=0.0.0.0"]
