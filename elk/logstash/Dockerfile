FROM docker.elastic.co/logstash/logstash:6.2.3

COPY ./logstash/pipeline/logstash.conf /usr/share/logstash/pipeline/logstash.conf
COPY ./logstash/wait-for-it.sh /usr/share/logstash/wait-for-it.sh

USER root
RUN chown logstash:logstash /usr/share/logstash/pipeline/logstash.conf \
    && chmod 0444 /usr/share/logstash/pipeline/logstash.conf \
    && chmod +x /usr/share/logstash/wait-for-it.sh
USER logstash
