# Configuration with Redis
* config file in `/usr/local/etc/redis/redis.conf`

## 1. Run after start Redis server
```
$docker container stop demo01
$docker container rm demo01

$docker container run --name demo01 -d redis:6
$docker container ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
7f0030709f52        redis:6             "docker-entrypoint.s…"   44 seconds ago      Up 43 seconds       6379/tcp            demo01

$docker container exec -it demo01 bash
>redis-benchmark -p 6379 -n 1000 -c 10 -k 1

>redis-cli --latency
>redis-cli --latency-dist

# Default configurations
>redis-cli
>config get *
```

## 2. Start with custom configurations
```
$docker container stop demo01
$docker container rm demo01

$docker container run --name demo01 -d \
  -v $(pwd)/redis.conf:/usr/local/etc/redis/redis.conf \
  redis:6 redis-server /usr/local/etc/redis/redis.conf

$docker container ps

$docker container exec -it demo01 bash
>redis-cli
>config get tcp*


```
