FROM docker.elastic.co/beats/heartbeat:6.3.0
COPY heartbeat.yml /usr/share/heartbeat/heartbeat.yml
USER root
RUN chown heartbeat /usr/share/heartbeat/heartbeat.yml
USER heartbeat

