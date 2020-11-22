## Working with [proxy caching](https://docs.konghq.com/hub/kong-inc/proxy-cache/)

### Step 1 :: Install plugin in Global scope
```
$curl -i -X POST http://127.0.0.1:8001/plugins \
--data name=proxy-cache \
--data config.content_type="application/json; charset=utf-8" \
--data config.cache_ttl=30 \
--data config.strategy=memory
```

Validate caching
```
$curl -i -X GET http://127.0.0.1:80/apis/users/1

X-Cache-Key: 7a4fa4231a51244862bbcafac15268e1
X-Cache-Status: Miss
X-Kong-Upstream-Latency: 551
X-Kong-Proxy-Latency: 1

```

### Step 2 :: Enable plugins
* On service
* On route
* O consumer

### Step 3 :: Delete plugin
```
$curl -i -X DELETE http://127.0.0.1:8001/proxy-cache
```

[Next :: Load balancing](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/05-load-balancing.md)
