## Working with [Rate Limit](https://docs.konghq.com/hub/kong-inc/rate-limiting/) of your APIs

### Step 1 :: Enable rate limit plugin in Global scope

Example :: 
* 5 minutes per minutes 
* Store data in a memory and local node

```
$curl -i -X POST http://127.0.0.1:8001/plugins \
--data name=rate-limiting \
--data config.minute=5 \
--data config.policy=local
```

Try call APIs from routes
```
$curl -i -X GET http://127.0.0.1:80/apis/users/1

X-RateLimit-Remaining-Minute: 4
X-RateLimit-Limit-Minute: 5
RateLimit-Remaining: 4
RateLimit-Limit: 5
RateLimit-Reset: 16


$curl 127.0.0.1

{
  "message":"API rate limit exceeded"
}
```

### Step 2 : Enable rate limit plugin with
* On service
* On route
* On consumer

On service
```
$curl -X POST http://<admin-hostname>:8001/services/<service>/plugins \
    --data "name=rate-limiting"  \
    --data "config.second=5" \
    --data "config.hour=10000" \
    --data "config.policy=local"
```

On route
```
$curl -X POST http://<admin-hostname>:8001/routes/<route>/plugins \
    --data "name=rate-limiting"  \
    --data "config.second=5" \
    --data "config.hour=10000" \
    --data "config.policy=local"
```

On consumer
```
$curl -X POST http://<admin-hostname>:8001/consumers/<consumer>/plugins \
    --data "name=rate-limiting"  \
    --data "config.second=5" \
    --data "config.hour=10000" \
    --data "config.policy=local"
```

[Next :: Proxy caching](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/04-proxy-cache.md)
