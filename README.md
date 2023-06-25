To bring up monitoring stack using docker 

#### 1. Prometheus

```
docker run -d --name prometheus-container -v /home/sndee/prometheus.yml:/etc/prometheus/prometheus.yml -e TZ=UTC -p 9090:9090 ubuntu/prometheus:2.33-22.04_beta
```

Note:- For more info [prometheus](https://hub.docker.com/r/ubuntu/prometheus)

#### 2. Grafana

```
docker run -d --name=grafana -p 3000:3000 grafana/grafana:8.5.5
```

Note:- For more info [Grafana](https://hub.docker.com/r/grafana/grafana)

#### 3. InfluxDb

```
docker run -d -p 8086:8086 --name influxdb2 influxdb:1.8.6-alpine
```

**Connect to container and execute below Influx Commands**
```
docker exec -it influxdb2 bash 
influx
CREATE DATABASE "jenkins" WITH DURATION 1825d REPLICATION 1 NAME "jenkins-retention"
SHOW DATABASES
USE <database_name>
```

![image](https://user-images.githubusercontent.com/29688323/218266342-da04d428-5e2f-4986-a68e-1d3789046eb5.png)

**Alerts**
```
docker run -d --name prometheus-alertmanager-container -e TZ=UTC -v /home/sndee/alertmanager.yml:/etc/alertmanager/alertmanager.yml -p 9093:9093 ubuntu/prometheus-alertmanager:0.23-22.04_beta
```

```
docker run -d --name prometheus-container -v /home/sndee/prometheus.yml:/etc/prometheus/prometheus.yml -v /home/sndee/prometheus_rules.yml:/etc/prometheus/prometheus_rules.yml -e TZ=UTC -p 9090:9090 ubuntu/prometheus:2.33-22.04_beta
```

```
SELECT count(build_number) FROM ( SELECT * FROM  "jenkins_data" WHERE ("project_name" =~ /^(?i)admin-api$/ AND "project_path" =~ /.*(?i)admin.*$/) ORDER BY time DESC LIMIT 10 ) WHERE ("build_result" = 'FAILURE' OR "build_result" = 'CompletedError' ) ORDER BY time DESC
```

```
docker run -d --name=grafana -p 3000:3000 -v /home/sndee/grafana.ini:/etc/grafana/grafana.ini grafana/grafana:8.5.5
```

