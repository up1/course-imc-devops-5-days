## Monitoring Kong with [Prometheus](https://docs.konghq.com/hub/kong-inc/prometheus/)

### Step 1 :: Enable plugin

```
// By service
$curl -X POST http://<admin-hostname>:8001/services/<service>/plugins \
    --data "name=prometheus"
    
// Global
curl -X POST http://<admin-hostname>:8001/plugins/ \
    --data "name=prometheus" 
```

Check Prometheus metric in URL = http://admin-hostname:8001:<port>/metrics


### [Grafana dash board](https://grafana.com/dashboards/7424)

