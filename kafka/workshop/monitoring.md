# Monitoring Kafka
* [JMX Exporter](https://github.com/prometheus/jmx_exporter)
  * Export metric from JMX (Java Management Extension)
* [Kafka Exporter](https://github.com/danielqsj/kafka_exporter)
  * Broker
  * Topic
  * Consumer

## Run Kafka exporter for Prometheus
```
docker-compose up -d kafka-exporter
docker-compose ps
docker-compose logs --follow
```

Check result in url = server-ip:9308
