FROM openjdk:8-jre-alpine
WORKDIR /app
ENV KAFKA_PORT 9092
ENV PATH="/app/utils:${PATH}"
COPY utils/ /app/utils/
COPY supervisord.conf /app/supervisord.conf
COPY configureKafka.sh /app/configureKafka.sh
RUN chmod a+x /app/configureKafka.sh && \ 
    chmod a+x /app/utils/* && \ 
    mkdir logs && \
    apk update && apk add bash && apk add libc6-compat && apk add supervisor && \
    wget "https://archive.apache.org/dist/kafka/0.10.1.1/kafka_2.11-0.10.1.1.tgz" && \
    tar xvzf kafka_2.11-0.10.1.1.tgz && rm kafka_2.11-0.10.1.1.tgz
CMD /usr/bin/supervisord -c /app/supervisord.conf