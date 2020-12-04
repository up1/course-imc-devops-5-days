# Monitoring Kafka
<<<<<<< HEAD
* [Kafka Exporter](https://github.com/danielqsj/kafka_exporter)
* [JMX Exporter](https://github.com/prometheus/jmx_exporter)

## Run Kafka exporter
=======
* [JMX Exporter](https://github.com/prometheus/jmx_exporter)
  * Export metric from JMX (Java Management Extension)
* [Kafka Exporter](https://github.com/danielqsj/kafka_exporter)
  * Broker
  * Topic
  * Consumer

## Run Kafka exporter for Prometheus
>>>>>>> d653ff095475b19e1981e4286bb040611e3a9493
```
docker-compose up -d kafka-exporter
docker-compose ps
docker-compose logs --follow
```

Check result in url = server-ip:9308
<<<<<<< HEAD

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
=======
>>>>>>> d653ff095475b19e1981e4286bb040611e3a9493
