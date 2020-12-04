# Monitoring Kafka
* [Kafka Exporter](https://github.com/danielqsj/kafka_exporter)
* [JMX Exporter](https://github.com/prometheus/jmx_exporter)

## Run Kafka exporter
```
docker-compose up -d kafka-exporter
docker-compose ps
docker-compose logs --follow
```

Check result in url = server-ip:9308

## Run JMX exporter

Configuration metrics of Kafka => `jmxexporter.yml`
```
---
startDelaySeconds: 3
hostPort: kafka:1099
username:
password:

whitelistObjectNames: ["kafka.server:type=BrokerTopicMetrics,*"]
rules:
  - pattern: ".*"
```

```
docker-compose up -d jmx-exporter
docker-compose ps
docker-compose logs --follow
```

Check result in url = server-ip:5556