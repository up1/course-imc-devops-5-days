# Introduction to Apache Kafka

## Start Kafka server + Zookeeper
```
docker-compose up -d zookeeper
docker-compose up -d kafka
docker-compose ps
docker-compose logs --follow
```

Scale Kafka
```
docker-compose scale kafka=3
```

## Hello Kafka
```
./start-kafka-shell.sh  <server ip 1>  zookeeper:2181
```
* server ip 1 = HOST_IP
* server ip 2 = ZK_IP

## Create new Topic = hello
```
$KAFKA_HOME/bin/kafka-topics.sh --create --topic hello --partitions 4 --zookeeper $ZK --replication-factor 1

// Describe topic = hello
$KAFKA_HOME/bin/kafka-topics.sh --describe --topic hello --zookeeper $ZK

// List all topics
$KAFKA_HOME/bin/kafka-topics.sh --list  --topic hello --zookeeper $ZK
```

## Producer
```
$KAFKA_HOME/bin/kafka-console-producer.sh --topic=hello --broker-list=`broker-list.sh`
>
```

## Working with Consumers

Consumer 1 in window 1
```
./start-kafka-shell.sh  <server ip>  <server ip>:2181

$KAFKA_HOME/bin/kafka-console-consumer.sh --topic=hello --from-beginning --bootstrap-server $HOST_IP:9092
```

Consumer 2 in window 2
```
./start-kafka-shell.sh  <server ip>  <server ip>:2181

$KAFKA_HOME/bin/kafka-console-consumer.sh --topic=hello --from-beginning --bootstrap-server $HOST_IP:9092
```

## Working Consumer groups

Group 1 in window 1
```
./start-kafka-shell.sh  <server ip>  <server ip>:2181

$KAFKA_HOME/bin/kafka-console-consumer.sh --topic=hello --group group1 --from-beginning --bootstrap-server $HOST_IP:9092

```

Group 1 in window 2
```
./start-kafka-shell.sh  <server ip>  <server ip>:2181

$KAFKA_HOME/bin/kafka-console-consumer.sh --topic=hello --group group1 --from-beginning --bootstrap-server $HOST_IP:9092

```


Group 2 in window 3
```
./start-kafka-shell.sh  <server ip>  <server ip>:2181

$KAFKA_HOME/bin/kafka-console-consumer.sh --topic=hello --group group2 --from-beginning --bootstrap-server $HOST_IP:9092

```
