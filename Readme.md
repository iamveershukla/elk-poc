# Overview
This repository contains an implementation of the Elastic Stack.  
- Elasticsearch
- Logstash
- Kibana
- Filebeat
- Metricbeat
- Heartbeat

# Instructions
1. [Download, Install and Run Docker](https://docs.docker.com/engine/installation/) using the instructions appropriate to your operating system.
2. Open a console window
3. Clone this repository
```bash
git clone https://github.com/iamveershukla/elk-poc.git
cd elk-poc
```
4. Create the docker image for spring-petclinic application
```bash
cd spring-petclinic
docker build -t spring-petclinic . 
```
5. Create the docker image for Filebeat
```bash
cd filebeat
docker build -t filebeat . 
```
6. Create the docker image for Logstash
```bash
cd ../logstash
docker build -t logstash . 
```
7. Create the docker image for Elasticsearch
```bash
cd ../elasticsearch
docker build -t elasticsearch . 
```
8. Create the docker image for Kibana
```bash
cd ../kibana
docker build -t kibana . 
```
9. Create the docker image for Metricbeat
```bash
cd ../metricbeat/system
docker build -t metricbeat-system . 
```
10. Create the docker image for Heartbeat
```bash
cd ../../heartbeat
docker build -t heartbeat . 
```
11. Start the spring-petclinic application
```bash
cd ../spring-petclinic
docker-compose up &
```
12. Start the elk-poc stack
```bash
cd ..
docker-compose up &
```

13. Start the heartbeat stack
```bash
cd ./heartbeat
docker-compose up &
```

14. Check the status of the running containers for elk-poc stack
```bash
cd ..
docker ps -a
```
15. Browse to http://localhost:8085/, this will display the home page of petclinic application.  Application logs from the petclinic application will be automatically forwarded to the Logstash server, where the records will be parsed and sent to Elasticsearch for indexing, they will also be written to standard output so they appear in the console window.

16. You can search Elasticsearch directly via its REST API.  Browse to http://localhost:9200/petclinic/_search?q=*. If you are prompted to login, use the default credentials, username: elastic, password: changeme. Note: by default, only 10 records will be returned, the search behavior is controlled via additional parameters to the search API.

17. Once the ELK stack starts up you can list all indices in elasticsearch using: http://localhost:9200/_cat/indices?v&pretty

18. You can search Elasticsearch visually, using Kibana. Browse to http://localhost:5601, when prompted to login, use the default credentials, username: elastic, password: changeme. 

19. Go to Management section, where you must configure an index pattern, this is where you will tell Kibana which Elasticsearch index to use.
Enter petclinic-* for the index name and then click the _Create_ button. 
Enter metricbeat-* for the index name and then click the _Create_ button. 
After successful configuration, you will see all of the fields that are searchable in the metricbeat-* and petclinic-* Kibana indices.




