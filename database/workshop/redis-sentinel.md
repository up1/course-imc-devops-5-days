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
$docker-compose -f docker-compose.sentinel.yml build 

# Start containers
$docker-compose -f docker-compose.sentinel.yml up -d 

$docker-compose -f docker-compose.sentinel.yml ps
```

