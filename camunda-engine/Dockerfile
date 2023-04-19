FROM gradle:7.2.0-jdk17 AS build
ARG BUILD_ENV
ENV ENVIRON=$BUILD_ENV
WORKDIR /usr/src/app
COPY . .
RUN ./gradlew clean build


FROM openjdk:17-jdk-slim
WORKDIR /usr/app
ARG BUILD_ENV
ENV ENVIRON=$BUILD_ENV
COPY --from=build /usr/src/app/build/libs/camunda-engine-0.0.1-SNAPSHOT.jar /usr/app/camunda-engine-0.0.1-SNAPSHOT.jar
EXPOSE 8081
CMD java -Dnewrelic.environment=${ENVIRON} -Djava.library.path=/usr/app/libs/linux-x86-64/ -Xms1536m -Xmx1536m -XX:NativeMemoryTracking=summary -jar -Dspring.profiles.active=${ENVIRON} camunda-engine-0.0.1-SNAPSHOT.jar