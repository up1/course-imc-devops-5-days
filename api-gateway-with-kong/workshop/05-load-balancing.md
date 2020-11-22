## Working with [Load balancing](https://docs.konghq.com/2.2.x/loadbalancing/)

### Step 1 :: Create upstream services
```
$curl -X POST http://127.0.0.1:8001/upstreams \
 --data name=upstream
```

### Step 2 :: Update services to point to upstream
```
$curl -X PATCH http://127.0.0.1:8001/services/demo_service \
 --data host='upstream'
```

### Step 3 :: Add 2 targets to upstream
```
$curl -X POST http://127.0.0.1:8001/upstreams/upstream/targets \
 --data target='jsonplaceholder.cypress.io:80'

$curl -X POST http://127.0.0.1:8001/upstreams/upstream/targets \
 --data target='jsonplaceholder.typicode.com:80'
```

### Step 4 :: Validate upstream
```
$curl -i -X GET http://127.0.0.1:80/apis/users/1
```

*** check `protocol=http` of Demo-service ***

[Next :: Basic authentication](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/06-authentication.md)
