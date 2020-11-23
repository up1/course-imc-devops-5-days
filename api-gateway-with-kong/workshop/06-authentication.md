# Working with Authentication

## Working with basic authentication

### Step 1 :: Add [basic-auth plugin](https://docs.konghq.com/hub/kong-inc/basic-auth/) to service
```
$curl -X POST http://http://127.0.0.1:8001/services/<service>/plugins \
    --data "name=basic-auth"  \
    --data "config.hide_credentials=true"
```

List of plugins
```
$curl --location --request GET 'http://127.0.0.1:8001/services/demo_service/plugins'
```

### Step 2 :: Create consumer
```
$curl -X POST http://http://127.0.0.1:8001/consumers \
    --data "username=demo-name"  \
    --data "custom_id=100"
```

List of all consumers
```
$curl --location --request GET 'http://127.0.0.1:8001/consumers'
```

### Step 3 :: Create credential
```
$curl -X POST 'http://127.0.0.1:8001/consumers/demo-name/basic-auth' \
  --header 'Content-Type: application/json' \
  --data "username=user01"  \
  --data "password=pass01"
```

### Step 4 :: Verify target with basic-auth
```
$curl --location --request GET 'http://127.0.0.1/apis/users' \
--header 'Authorization: Basic dXNlcjAxOnBhc3MwMQ=='
```

[Next :: Logging with ELK stack](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/07-logging.md)
