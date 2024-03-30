Need to have or set a hostname

docker network create grafana_prometheus        

docker run --rm --name grafana --network grafana_prometheus --publish 3000:3000 --detach grafana/grafana-oss:latest

docker run --rm --name my-prometheus --network grafana_prometheus --publish 9090:9090 --volume ${PWD}/prometheus.yml:/etc/prometheus/prometheus.yml --detach prom/prometheus