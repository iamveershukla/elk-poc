FROM docker.elastic.co/beats/metricbeat:6.3.0

COPY metricbeat.yml /usr/share/metricbeat/metricbeat.yml
USER root
RUN chown metricbeat /usr/share/metricbeat/metricbeat.yml
USER metricbeat

