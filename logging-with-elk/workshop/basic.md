# Cluster, Node and Index

## Checking the cluster's health
```
GET /_cluster/health
```

## Listing the cluster's [nodes](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html)
```
GET /_cat
GET /_cat/nodes?v
```

[Node roles](https://www.elastic.co/guide/en/elasticsearch/reference/current/cat-nodes.html)
* c = cold node
* d = data node
* h = hot node
* i = ingest node
* l = machine learning node
* m = master-eligible node
* r = remote cluster client node
* s = content node
* t = transform node
* w = warm node
* v = voting-only node
* `-` = coordinating node only

## Listing the cluster's indices
```
GET /_cat/indices?v
```

## Checking the shard distribution
```
GET /_cat/shards?v
```
