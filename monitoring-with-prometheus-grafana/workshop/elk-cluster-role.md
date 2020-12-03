# Elasticsearch cluster

## Simple cluster with [node roles](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html) and [Data Tier](https://www.elastic.co/guide/en/elasticsearch/reference/master/data-tiers.html#hot-tier)
* es01 => Master node
* es02 => Data node
* es03 => Hot node (For indexing and search for tike-series data)
```
$docker-compose -f docker-compose-elk-02.yml up -d
$docker-compose -f docker-compose-elk-02.yml ps

Name              Command               State                Ports
--------------------------------------------------------------------------------
es01   /tini -- /usr/local/bin/do ...   Up      0.0.0.0:9200->9200/tcp, 9300/tcp
es02   /tini -- /usr/local/bin/do ...   Up      9200/tcp, 9300/tcp
es03   /tini -- /usr/local/bin/do ...   Up      9200/tcp, 9300/tcp
```

Check nodes in cluster
* http://server-ip:9200/_cat/nodes?v

```
ip          heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
192.168.0.5           26          97  49    6.10    3.77     2.10 m         *      es01
192.168.0.3           66          97  50    6.10    3.77     2.10 d         -      es02
192.168.0.2           56          97  68    6.10    3.77     2.10 h         -      es03
```

Remove all containers and volumes
```
$docker-compose -f docker-compose-elk-02.yml ps

$docker volume ls
$docker volume prune -f
```
