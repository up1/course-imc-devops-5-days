# Working with [Prometheus Alertmanager](https://grafana.com/blog/2020/02/25/step-by-step-guide-to-setting-up-prometheus-alertmanager-with-slack-pagerduty-and-gmail/)

## Steps
* Create alert rules in Prometheus
* Setup Alertmanager
  * Receivers the alerts specified in Prometheus
  * Send alert/notification to target system (e.g. Email, Slack, LINE, other systems)

## 1. Create alert rules in Prometheus
Edit in file `prometheus/alert.rules`

```
groups:
- name: AllInstances
  rules:
  - alert: InstanceDown
    # Condition for alerting
    expr: up == 0
    for: 1m
    # Annotation - additional informational labels to store more information
    annotations:
      title: 'Instance {{ $labels.instance }} down'
      description: '{{ $labels.instance }} of job {{ $labels.job }} has been down for more than 1 minute.'
    # Labels - additional labels to be attached to the alert
    labels:
        severity: 'critical'
```

### Example of Alert rules
* https://awesome-prometheus-alerts.grep.to/
* https://github.com/samber/awesome-prometheus-alerts
* https://github.com/roaldnefs/awesome-prometheus


## 2. Setup alert.rules in Prometheus server
Edit in file `prometheus/prometheus.yml`
```
global:
  scrape_interval: 5s
  evaluation_interval: 5s

  # added when sending things to external systems (alerts)
  external_labels:
    monitor: 'devops'

# Load and evaluate rules in this file every 'evaluation_interval' seconds.
rule_files:
  - "alert.rules"

# alert
alerting:
  alertmanagers:
  - scheme: http
    static_configs:
    - targets:
      - "alertmanager:9093"
```

## 3. Setup Alertmanager
* [PagerDuty](https://www.pagerduty.com/)
* [Slack webhooks](https://slack.com/intl/en-th/help/articles/115005265063-Incoming-webhooks-for-Slack)
* [LINE Bot](https://line.me/en/)
* Zabbix
  * [Using web hooks](https://prometheus.io/docs/alerting/latest/configuration/#webhook_config)
  * [Reference](https://devopy.io/setting-up-zabbix-alertmanager-integration/)


## PagerDuty
```
global:
 resolve_timeout: 1m
 pagerduty_url: 'https://events.pagerduty.com/v2/enqueue'

route:
  receiver: 'pagerduty-notifications'

receivers:
- name: 'pagerduty-notifications'
  pagerduty_configs:
  - service_key: <api-key>
    send_resolved: true
```

## Slack webhooks
* [Setup slack app](https://api.slack.com/apps)
```
global:
 resolve_timeout: 1m
 slack_api_url: 'hook url'

route:
  receiver: 'slack-notifications'

receivers:
- name: 'slack-notifications'
  slack_configs:
  - channel: '#monitoring'
    send_resolved: true
```

## 4. Start workshop of Alertmanager
* Node exporter
* Alert manager
* Prometheus

```
$docker-compose up -d node-exporter
$docker-compose up -d alertmanager
$docker-compose up -d prometheus

$docker-compose ps
$docker-compose logs --follow
```

Check data 
* Endpoint of Node Expoter = http://server-ip:9100
* Alert Manager UI = http://server-ip:9093
* Prometheus UI = http://server-ip:9090

