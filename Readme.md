# Overview
This repository contains an implementation of the Elastic Stack.  
- **E**lasticsearch
- **L**ogstash
- **K**ibana
- Beats

# Instructions
1. [Download, Install and Run Docker](https://docs.docker.com/engine/installation/) using the instructions appropriate to your operating system.
2. Open a console window
3. Clone this repository
```bash
git clone https://github.com/iamveershukla/elk-poc.git
cd elk-poc
```
4. Create the docker container spring-petclinic application
```bash
cd spring-petclinic
docker build -t spring-petclinic . 
```
5. Create the docker container containing Filebeat
```bash
cd filebeatApacheDocker
docker build -t filebeat . 
```
6. Create the docker container containing Logstash
```bash
cd ../logstashDocker
docker build -t logstash . 
```
7. Create the docker container containing Elasticsearch
```bash
cd ../elasticsearchDocker
docker build -t elasticsearch . 
```
8. Create the docker container containing Kibana
```bash
cd ../kibanaDocker
docker build -t kibana . 
```
9. Start the elk-poc stack
```bash
cd ..
docker-compose up &
```

10. Check the status of the running containers for elk-poc stack
```bash
cd ..
docker ps -a
```
11. Browse to http://localhost:8085/, this will display the home page of petclinic application.  Application logs from the petclinic application will be automatically forwarded to the Logstash server, where the records will be parsed and sent to Elasticsearch for indexing, they will also be written to standard output so they appear in the console window.

12. You can search Elasticsearch directly via its REST API.  Browse to http://localhost:9200/petclinic/_search?q=*. If you are prompted to login, use the default credentials, username: _elastic_, password: _changeme_. Note: by default, only 10 records will be returned, the search behavior is controlled via additional parameters to the search API.

13. You can search Elasticsearch visually, using Kibana. Browse to http://localhost:5601, when prompted to login, use the default credentials, username: _elastic_, password: _changeme_. You will land in the Management section, where you must configure an index pattern, this is where you will tell Kibana which Elasticsearch index to use, enter petclinic for the index name and then click the _Create_ button. Upon successful configuration, you will see all of the fields that are searchable in the _elk-poc_ index.

14. To shutdown the elk-poc stack, press `Ctrl-c` in the console window.



