## Working with Rate Limit of your APIs

### Step 1 :: Enable rate limit plugin

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
$curl 127.0.0.1

{
  "message":"API rate limit exceeded"
}
```
