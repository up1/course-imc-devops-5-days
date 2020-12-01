## Install ELK with Docker (Single node)

Start [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)
```
$docker-compose up -d elasticsearch
$docker-compose ps
$docker-compose logs --follow
```

Start Kibana
```
$docker-compose up -d kibana
$docker-compose ps
$docker-compose logs --follow
```

* Check elasticsearch => server-ip:9200
* Check kibana => server-ip:5601

Start Logstash with Sample Data
```
$docker-compose up -d logstash
$docker-compose ps
$docker-compose logs --follow
```

Check data in Elasticsearch
* server-ip:9200/_cat/indices
* server-ip:9200/logstash/_search
