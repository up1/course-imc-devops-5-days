## Logging with ELK stack by using [UDP log plugin](https://docs.konghq.com/hub/kong-inc/udp-log/)

### Step 1 :: Install Logstash

```
$docker-compose up -d elasticsearch
$docker-compose up -d logstash
$docker-compose ps

$docker-compose logs --follow elasticsearch
$docker-compose logs --follow logstash
```

Access to elasticsearch container
```
$docker-compose exec elasticsearch bash
>curl 127.0.0.1:9200
>curl 127.0.0.1:9200/_cat/indices
```

### Step 2 :: Enable UDP log plugin in global scope
```
$curl -X POST http://127.0.0.1:8001/plugins/ \
    --data "name=udp-log"  \
    --data "config.host=logstash" \
    --data "config.port=5000"
```
