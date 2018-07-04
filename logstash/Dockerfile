FROM docker.elastic.co/logstash/logstash:6.3.0

# place our logstash pipeline configuration
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
ADD logstash.conf /usr/share/logstash/pipeline/logstash.conf

RUN mkdir /usr/share/logstash/pipeline/patterns
ADD custom-patterns.conf /usr/share/logstash/pipeline/patterns/custom-patterns.conf

EXPOSE 5043
