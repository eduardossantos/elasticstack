# https://github.com/elastic/elasticsearch-docker
FROM docker.elastic.co/elasticsearch/elasticsearch:6.2.3

COPY ./elasticsearch/config/limits.conf /etc/security/limits.conf
COPY ./elasticsearch/config/elasticsearch.yml /config/elasticsearch.yml

# Add your elasticsearch plugins setup here
# Example: RUN elasticsearch-plugin install analysis-icu
USER root
RUN set -ex \
    cd /usr/share/elasticsearch \
    && for path in \
        ./data \
        ./logs \
        ./config \
        ./config/scripts \
    ; do \
        mkdir -p "$path"; \
        chown -R elasticsearch:root "$path"; \
    done \
    && chown -R elasticsearch:root /etc/security/ /config/elasticsearch.yml
