# Kafka monitoring

## Setup (Prometheus - JMX Exporter)

Download `jmx_prometheus_javaagent-VERSION.jar` to `jmx-exporter` directory.

`curl -L -o jmx-exporter/jmx_prometheus_javaagent.jar https://github.com/prometheus/jmx_exporter/releases/download/1.5.0/jmx_prometheus_javaagent-1.5.0.jar`

See for more details and new versions: [Prometheus - JMX Exporter](https://prometheus.github.io/jmx_exporter/)


## Usage

1. Run `docker compose up -d` (`docker compose stop` or `docker compose down`)
2. Check status of containers `docker ps` (`docker ps -a`)
    - Debugging: `docker logs CONTAINER_ID`
3. UIs
    - [Grafana](http://localhost:3000/) (compose/cluster hostname: http://grafana:3000/)
        - Login
            - Username: `admin`
            - Password: `grafana`
        - use **prometheus** datasource (see `grafana/datasources/init.yaml`)
    - [Prometheus](http://localhost:9090/) (compose/cluster hostname: http://prometheus:9090/)


## Basic Kafka CLI commands

- `KAFKA_OPTS="" kafka-topics.sh --bootstrap-server localhost:9092 --list`
- `KAFKA_OPTS="" bin/kafka-topics.sh --bootstrap-server localhost:9092 --list`
- `KAFKA_OPTS="" bin/kafka-topics.sh --create --topic test --bootstrap-server localhost:9092`
- `KAFKA_OPTS="" bin/kafka-console-producer.sh --topic test --bootstrap-server localhost:9092`
- `KAFKA_OPTS="" bin/kafka-console-consumer.sh --topic test --from-beginning --bootstrap-server localhost:9092`
- `KAFKA_OPTS="" bin/kafka-consumer-groups.sh --list --bootstrap-server localhost:9092`
- `KAFKA_OPTS="" bin/kafka-consumer-groups.sh --describe --group mygroup --bootstrap-server localhost:9092`

