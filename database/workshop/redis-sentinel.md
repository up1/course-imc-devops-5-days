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

Default configurations
* SENTINEL_QUORUM: 2
* SENTINEL_DOWN_AFTER: 5000
* SENTINEL_FAILOVER: 5000


```
# Build image
$docker-compose -f docker-compose.sentinel.yml build 

# Start containers
$docker-compose -f docker-compose.sentinel.yml up -d 

$docker-compose -f docker-compose.sentinel.yml ps
       Name                      Command               State    Ports
-----------------------------------------------------------------------
workshop_master_1     docker-entrypoint.sh redis ...   Up      6379/tcp
workshop_sentinel_1   entrypoint.sh                    Up      6379/tcp
workshop_slave_1      docker-entrypoint.sh redis ...   Up      6379/tcp
```

## Scale number of sentinel nodes
```
$docker-compose -f docker-compose.sentinel.yml scale sentinel=3
```

## Scale number of slave nodes
```
$docker-compose -f docker-compose.sentinel.yml scale slave=3
```

## Get information of sentinel
```
$docker-compose -f docker-compose.sentinel.yml exec sentinel redis-cli -p 26379 SENTINEL get-master-addr-by-name mymaster
```
