# Working with Prometheus
Prometheus is a monitoring system prepared for dynamic environments.
* based on metrics
* dimensional data model
* query language
* build-in service discovery
* simple and efficient components

## Prometheus workshop
* Node exporter
* Alert manager
* Prometheus
```
$docker-compose up -d node-exporter
$docker-compose up -d mailhog
$docker-compose up -d alertmanager
$docker-compose up -d prometheus

$docker-compose ps
$docker-compose logs --follow
```

Check data 
* Endpoint of Node Expoter = http://server-ip:9100
* Alert Manager UI = http://server-ip:9093
* Prometheus UI = http://server-ip:9090

## Grafana workshop
```
$docker-compose up -d grafana

$docker-compose ps
$docker-compose logs --follow
```

Grafana UI = http://server-ip:3000

## Using [CAdvisor](https://github.com/google/cadvisor)
```
$docker-compose up -d cadvisor

$docker-compose ps
$docker-compose logs --follow
```

CAdvisor UI = http://server-ip:8080