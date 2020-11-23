## Install Kong and Konga

### Step 1 :: Setup database (PostgreSQL)

```
$docker-compose up -d kong-database
$docker-compose ps
```

### Step 2 :: Migrate database of Kong

```
$docker-compose up migrations
$docker-compose ps
```

Access to database
```
$docker-compose exec kong-database bash
$psql -U kong -W
```


### Step 3 :: Install Kong server

```
$docker-compose up -d kong
$docker-compose ps
```

Open Kong Admin APIs at `http://127.0.0.1:8001`

### Step 4 :: Install [Konga (GUI Admin)](https://github.com/pantsel/konga)

```
$docker-compose up -d mongo
$docker-compose up -d konga
```

Open Konga GUI at `http://127.0.0.1:1337`
* Name=Kong
* Kong Admin URL=http://kong:8001

[Next :: Create services and routes](https://github.com/up1/course-imc-devops-5-days/blob/main/api-gateway-with-kong/workshop/02-create-service-and-route.md)
