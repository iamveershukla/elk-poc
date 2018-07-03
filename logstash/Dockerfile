FROM docker.elastic.co/logstash/logstash:6.3.0

# place our logstash pipeline configuration
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
ADD logstash.conf /usr/share/logstash/pipeline/

EXPOSE 5043
