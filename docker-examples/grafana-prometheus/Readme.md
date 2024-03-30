# Simple Grafana-Prometheus Docker Networking 

## This is a simple project to check how dockerized prometheus works with dockerized grafana over a network

> It is required to setup a hostname else one can always check hostname
> by typing "hostname" on mac/linux based machines


```
docker network create grafana_prometheus        
```

```
docker run --rm --name my-prometheus --network grafana_prometheus --publish 9090:9090 --volume ${PWD}/prometheus.yml:/etc/prometheus/prometheus.yml --detach prom/prometheus
```


```
docker run --rm --name grafana --network grafana_prometheus --publish 3000:3000 --detach grafana/grafana-oss:latest
```