FROM schoolofdevops/maven as build
WORKDIR /app
COPY .  .
RUN mvn package


FROM openjdk:8-jdk as package
ARG user=app
ARG group=app
ARG uid=1000
ARG gid=1000

RUN groupadd -g ${gid} ${group} \
    && useradd  -u ${uid} -g ${gid} -m -s /bin/bash ${user}

COPY --from=build /app/target/worker-jar-with-dependencies.jar  /run/worker.jar

RUN chown ${user}:${group} /run/worker.jar

USER ${user}

CMD java  -jar /run/worker.jar
