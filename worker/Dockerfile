FROM schoolofdevops/maven

WORKDIR /app

COPY .  .

RUN mvn package && \
    mv target/worker-jar-with-dependencies.jar /run/worker.jar && \
    rm -rf /app/*

RUN chown -R ${user} /run/worker.jar

CMD java  -jar /run/worker.jar
