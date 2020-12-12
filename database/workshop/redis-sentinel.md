# [Redis Sentinel](https://redis.io/topics/sentinel)
Designed for high availability

## Node roles
* Master node for write data
* Slave node for read data

## Responsesibiliries
* Monitoring for (Master and Slave nodes)
* Notification to external systems (Prometheus, Grafana, NewRelic .. etc.)
* Automatic failover
* Configuration provider


## Sentinel
Required minimum nodes = 3 nodes
* Master = 1
* Slave = 2


```
# Build image
$docker-compose build

# Start containers
$docker-compose up -d

$docker-compose ps
```

