# Redis workshop with [Docker](https://hub.docker.com/_/redis)
* Single instance
* Sentinel
* Cluster

## Single instance
Required  1 nodes

```
# Create container from Redis image
$docker image pull redis:6
$docker container run --name demo01 -d redis:6

$docker container ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
012918047c96        redis:6             "docker-entrypoint.s…"   4 seconds ago       Up 3 seconds        6379/tcp            demo01

# Access to container
$docker container exec -it demo01 bash
>redis-cli
127.0.0.1:6379>
```

## Workshop with Redis commands
```
// See all keys (don't use in production !!)
>keys *
```

[String opertation](https://redis.io/commands#string)
```
>set name pui
>get name
>keys *

>set counter 1
>INCR counter
>INCRBY counter 5
```
[List operation](https://redis.io/commands#list)
```
>lpush numbers 1
>lpush numbers 2
>lpush numbers 3
>lpush numbers 4

>LRANGE numbers 0 -1
```
[Hash operation](https://redis.io/commands#hash)
```
>HSET user1 id 1
>HSET user1 name "pui"
>HSET user1 age 30

>HGETALL user1
>HKEYS user1
>HGET user1 name

```


