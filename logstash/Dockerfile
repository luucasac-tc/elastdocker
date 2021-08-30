# ARG ELK_VERSION

# https://github.com/elastic/logstash-docker
FROM docker.elastic.co/logstash/logstash:7.14.0

HEALTHCHECK --interval=240s --timeout=120s --retries=5 \
  CMD curl -s -XGET 'http://127.0.0.1:9600'


# Add logstash plugins setup 
RUN logstash-plugin install logstash-input-http_poller
RUN logstash-plugin install logstash-input-mongodb
RUN logstash-plugin install logstash-input-google_pubsub
RUN logstash-plugin install logstash-filter-mutate
RUN logstash-plugin install logstash-filter-fingerprint

# copying file to container
COPY config/ logstash/config/
COPY pipeline/ pipeline/