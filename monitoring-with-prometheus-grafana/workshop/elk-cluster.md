# Elasticsearch cluster with [Docker](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html)

## Simple cluster (Default roles in 3 nodes)
```
$sysctl -w vm.max_map_count=262144
$docker-compose -f docker-compose-elk-01.yml up -d
$docker-compose -f docker-compose-elk-01.yml ps

Name              Command               State                Ports
--------------------------------------------------------------------------------
es01   /tini -- /usr/local/bin/do ...   Up      0.0.0.0:9200->9200/tcp, 9300/tcp
es02   /tini -- /usr/local/bin/do ...   Up      9200/tcp, 9300/tcp
es03   /tini -- /usr/local/bin/do ...   Up      9200/tcp, 9300/tcp
```

Check nodes in cluster
* http://server-ip:9200/_cat/nodes?v

```
ip         heap.percent ram.percent cpu load_1m load_5m load_15m node.role  master name
172.20.0.4           20          93  86    5.05    1.40     0.48 cdhilmrstw *      es01
172.20.0.2           66          93  86    5.05    1.40     0.48 cdhilmrstw -      es02
172.20.0.3           59          93  86    5.05    1.40     0.48 cdhilmrstw -      es03
```

Remove all containers and volumes
```
$docker-compose -f docker-compose-elk-01.yml ps

$docker volume ls
$docker volume prune -f
```
