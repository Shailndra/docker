# Simple Grafana-Prometheus Docker Networking 

## This is a simple project to check how dockerized prometheus works with dockerized grafana over a network

> It is required to setup a hostname else one can always check hostname
> by typing "hostname" on mac/linux based machines

### Creating a docker netowk

```
docker network create grafana_prometheus        
```

### Running prometheus on docker with docker network created

```
docker run --rm --name my-prometheus --network grafana_prometheus --publish 9090:9090 --volume ${PWD}/prometheus.yml:/etc/prometheus/prometheus.yml --detach prom/prometheus
```

### Running grafana on docker with docker network created

```
docker run --rm --name grafana --network grafana_prometheus --publish 3000:3000 --detach grafana/grafana-oss:latest
```
### Check if the containers are up and running

```
docker ps 
```

### Once the containers are up and running

>Log into Grafana (default username "admin" and password "admin").
>Go to Configuration > Data sources
>Click Add data source
>Pick Prometheus as the data type
>Set the URL as http://hostname:9090 and click Save & test down the bottom.
