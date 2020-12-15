# Redis monitoring
1. Using Redis CLI
2. [Redis exporter with Prometheus](https://github.com/oliver006/redis_exporter)


# 1. Using Redis CLI
```
>redis-cli 
>info
>info server
>info clients
>info memory
>info persistence
>info stats
>info replication
>info cpu
>info commandstats
>info cluster
>info keyspace
```

## Top redis performance metrics
#### 1. Memory Usage => `used_memory`, `used_memory_human`
The	`used_memory metric` reports the total number of bytes allocated by Redis.

```
>info memory

used_memory:896776
used_memory_human:875.76K
```

Tips
* Set expirations for keys
* Evict keys (config set maxmemory value)
  * value = % of available memory
  * config `maxmemory-policy` in [redis.conf](https://github.com/up1/course-imc-devops-5-days/blob/main/database/workshop/example-redis.conf)

```
>info stats

expired_keys:0
evicted_keys:0
```

#### 2. Number of commands processed => `total_commands_processed`
The `total_commands_processed` metric gives the number of commands processed by the Redis server.

```
>info stats

total_commands_processed:40019

> SLOWLOG HELP
```

Tips
* Use multi-argument commands
  * SET -> MSET
  * GET -> MGET
* Use [pipeline command](https://redis.io/topics/pipelining)
* Avoid slow commands for large sets (Big-O notation)

#### 3. Latency + slowlog
Latency measures the average time in milliseconds it takes the Redis server to respond.

```
>redis-cli --latency -h host -p port
```
Tips
* Identify slow commands using slow log
* Monitoring client connection
* Limit client connections (`maxclients` in redis.conf)
* Improve memoru management (Swapping will significantly increase latency)
* Metric correlation

```
>info clients

connected_clients:4

> SLOWLOG HELP
```

#### 4. Memory Usage => `mem_fragmentation_ratio` = (OS/Redis)

#### 5. Evictions keys
* config `maxmemory` in [redis.conf](https://github.com/up1/course-imc-devops-5-days/blob/a0e0ab7b575a48b49a322b470c858ec821beae9e/database/workshop/example-redis.conf#L835)
* config `maxmemory-policy` in [redis.conf](https://github.com/up1/course-imc-devops-5-days/blob/a0e0ab7b575a48b49a322b470c858ec821beae9e/database/workshop/example-redis.conf#L835)

Tips
* Increase `maxmemory` limit
* [Partition your instance](https://redis.io/topics/partitioning)
  * Client side partition
  * Proxy assisted partition
  * Query routing
  * Redis Cluster

# 2. Redis Exporter

```
$docker-compose -f docker-compose-single.yml ps

          Name                         Command               State           Ports
-------------------------------------------------------------------------------------------
workshop_prometheus_1       /bin/prometheus --config.f ...   Up      0.0.0.0:9090->9090/tcp
workshop_redis-exporter_1   /redis_exporter                  Up      0.0.0.0:9121->9121/tcp
workshop_redis1_1           docker-entrypoint.sh redis ...   Up      6379/tcp
```

List of URL
* Redis exporter = http://server-ip:9121
* Prometheus server = http://server-ip:9090
