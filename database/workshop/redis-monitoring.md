# Redis monitoring
* Using Redis CLI
* [Redis exporter with Prometheus](https://github.com/oliver006/redis_exporter)


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
#### 1. Memory Usage => used_memory, used_memory_human
The	used_memory metric reports the total number of bytes allocated by Redis.

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

#### 2. Number of commands processed => total_commands_processed


#### 3. Latency + slowlog


#### 4. Memory Usage => mem_fragmentation_ratio = (OS/Redis)


#### 5. Evictions keys
Config `maxmemory-policy` in [redis.conf](https://github.com/up1/course-imc-devops-5-days/blob/main/database/workshop/example-redis.conf)
