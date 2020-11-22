# Working with Authentication

## Working with basic authentication

### Step 1 :: Add [basic-auth plugin](https://docs.konghq.com/hub/kong-inc/basic-auth/) to service
```
$curl --location --request POST 'http://127.0.0.1:8001/services/demo_service/plugins' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "basic-auth"
}'
```

List of plugins
```
$curl --location --request GET 'http://127.0.0.1:8001/services/demo_service/plugins'
```

### Step 2 :: Create consumer
```
$curl --location --request POST 'http://127.0.0.1:8001/consumers' \
--header 'Content-Type: application/json' \
--data-raw '{
	"username": "demo-name",
	"custom_id": "100"
}'
```

List of all consumers
```
$curl --location --request GET 'http://127.0.0.1:8001/consumers'
```

### Step 3 :: Create credential
```
$curl --location --request POST 'http://127.0.0.1:8001/consumers/demo-name/basic-auth' \
--header 'Content-Type: application/json' \
--data-raw '{
	"username": "user01",
	"password": "pass01"
}'
```

### Step 4 :: Verify target with basic-auth
```
$curl --location --request GET 'http://127.0.0.1/apis/users' \
--header 'Authorization: Basic dXNlcjAxOnBhc3MwMQ=='
```

[Next :: Logging with ELK stack](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/07-logging.md)
