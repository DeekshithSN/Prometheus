To bring up monitoring stack using docker 

#### 1. Prometheus

```
docker run -d --name prometheus-container -v /home/sndee/prometheus.yml:/etc/prometheus/prometheus.yml -e TZ=UTC -p 30090:9090 ubuntu/prometheus:2.33-22.04_beta
```

Note:- For more info [prometheus](https://hub.docker.com/r/ubuntu/prometheus)
