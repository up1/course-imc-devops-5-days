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
#### 1. Memory Usage => used_memory


#### 2. Number of commands processed => total_commands_processed


#### 3. Latency + slowlog


#### 4. Memory Usage => mem_fragmentation_ratio = (OS/Redis)


#### 5. Evictions keys
