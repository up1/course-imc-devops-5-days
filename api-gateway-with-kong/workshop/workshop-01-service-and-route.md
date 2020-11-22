# Workshop

## Create services

```
$curl -i -X POST http://127.0.0.1:8001/services \
 --data name=demo_service \
 --data url='https://jsonplaceholder.cypress.io'
```

Verify services
```
$curl -i http://127.0.0.1:8001/services/demo_service
```

## Add route to services
```
$curl -i -X POST http://127.0.0.1:8001/services/demo_service/routes \
  --data 'paths[]=/apis' \
  --data name=apis

$curl -i -X GET http://127.0.0.1:8001/routes
```

Verify routes is forwarding requests to the targer service
```
$curl -i -X GET http://127.0.0.1:80/apis/users/
$curl -i -X GET http://127.0.0.1:80/apis/users/1
```