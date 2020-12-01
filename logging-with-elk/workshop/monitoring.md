# [Monitoring Elasticsearch](https://www.elastic.co/what-is/elasticsearch-monitoring)
* [Working with Filebeat](https://www.elastic.co/guide/en/elasticsearch/reference/current/configuring-filebeat.html)
* [Working with MetricBeat](https://www.elastic.co/guide/en/elasticsearch/reference/current/configuring-metricbeat.html)


![](https://www.elastic.co/guide/en/elasticsearch/reference/current/monitoring/images/metricbeat.png)

## Working with Filebeat
```
$docker-compose up -d filebeat
$docker-compose ps
$docker-compose logs --follow
```

## Working with MetricBeat

```
$docker-compose up -d metricbeat
$docker-compose ps
$docker-compose logs --follow
```
