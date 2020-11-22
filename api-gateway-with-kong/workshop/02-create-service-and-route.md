## Create service and route

### Step 1 :: Create service
```
$curl 127.0.0.1:8001/services -d 'name=httpbin' -d 'url=http://httpbin.org'
```

Formatting JSON with [jq](https://stedolan.github.io/jq/)
```
$curl 127.0.0.1:8001/services -d 'name=httpbin2' -d 'url=http://httpbin.org' | jq

{
  "host": "httpbin.org",
  "id": "587443ec-56c6-4949-b5d1-5bc23f38a10f",
  "protocol": "http",
  "read_timeout": 60000,
  "tls_verify_depth": null,
  "port": 80,
  "updated_at": 1606032988,
  "ca_certificates": null,
  "created_at": 1606032988,
  "connect_timeout": 60000,
  "write_timeout": 60000,
  "name": "httpbin2",
  "retries": 5,
  "path": null,
  "tls_verify": null,
  "tags": null,
  "client_certificate": null
}
```

List all services
```
$curl 127.0.0.1:8001/services
```

### Step 2 :: Create route

```
$curl 127.0.0.1:8001/services/httpbin/routes -d 'paths[]=/'
```

List all routes
```
$curl 127.0.0.1:8001/routes
```


### Step 3 :: Testing with route

```
$curl 127.0.0.1
```


### Step 4 :: Delete services and routes

Delete route
```
$curl -X DELETE 'http://127.0.0.1:8001/routes/<route-id>'
```

Delete service
```
$curl -X DELETE 'http://127.0.0.1:8001/services/<service-id>'
```

[Next :: Rate Limit your API](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/03-rate-limit.md)
