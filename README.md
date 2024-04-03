# ELK based dashboards for 
This is community supported repo providing ELK based dashboards 

## How does it work?
ELK stands for elasticsearch, logstash, and kibana. Logstash receives logs from the F5 WAF, normalizes them and stores them in the elasticsearch index. Kibana allows you to visualize and navigate through logs using purpose built dashboards.

## Requirements
The provided Kibana dashboards require a minimum version of 7.4.2. If you are using the provided [docker-compose.yaml](docker-compose.yaml) file, this version requirement is met.

## Installation Overview
It is assumed you will be running ELK using the Quick Start directions below. The template in "logstash/conf.d" will create a new logstash pipeline to ingest logs and store them in elasticsearch. If you use the supplied `docker-compose.yaml`, this template will be copied into the docker container instance for you. Once the WAF logs are being ingested into the index, you will need to import files from the [kibana](kibana/) folder to create all necessary objects including the index pattern, visualization and dashboards.

## Quick Start
### Deploying ELK Stack
Use docker-compose to deploy your own ELK stack.
```
$ docker-compose -f docker-compose.yaml up -d
```

---
**NOTE**

The ELK stack docker container will likely exceed the default host's virtual memory system limits. Use [these directions](https://www.elastic.co/guide/en/elasticsearch/reference/5.0/vm-max-map-count.html#vm-max-map-count) to increase this limit on the docker host machine. If you do not, the ELK container will continually restart itself and never fully initialize.

---
