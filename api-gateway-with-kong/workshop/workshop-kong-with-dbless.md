## Working with Kong DB-less

### Step 1 :: Create Kong server with DB-less

```
$cd dbless
$docker-compose up -d
$docker-compose ps
$docker-compose logs --follow
```

Kong server
* [Kong Admin API in port 8001](http://127.0.0.1:8001)
* [Kong Proxy in port 80](http://127.0.0.1)
