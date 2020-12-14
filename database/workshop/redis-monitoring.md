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
* Memory Usage => used_memory
* Number of commands processed => total_commands_processed
* Latency + slowlog
* Memory Usage => mem_fragmentation_ratio = (OS/Redis)
* Evictions