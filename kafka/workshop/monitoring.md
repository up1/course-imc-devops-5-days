# Monitoring Kafka
* [JMX Exporter](https://github.com/prometheus/jmx_exporter)
* [Kafka Exporter](https://github.com/danielqsj/kafka_exporter)


## Run Kafka exporter for Prometheus
```
docker-compose up -d kafka-exporter
docker-compose ps
docker-compose logs --follow
```

Check result in url = server-ip:9308