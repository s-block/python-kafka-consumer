# Kafka consumer

## Setup
```bash
pyenv install 3.8.1
pyenv virtualenv 3.8.1 kc
pyenv shell kc
```

## Test
```bash
pytest
```


### Run Kafka
https://kafka.apache.org/quickstart

From Docker:
```bash
docker run -p 2181:2181 -p 9092:9092 --env ADVERTISED_HOST=`docker-machine ip \`docker-machine active\`` --env ADVERTISED_PORT=9092 spotify/kafka
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' {CONTAINER_NAME}
/opt/kafka_2.11-0.10.1.0/bin/kafka-topics.sh --create --replication-factor 1 --partitions 1 --topic {{topic}} --zookeeper localhost:2181
```

Locally:
https://medium.com/@Ankitthakur/apache-kafka-installation-on-mac-using-homebrew-a367cdefd273
```bash
brew cask install java
brew install kafka
zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties & kafka-server-start /usr/local/etc/kafka/server.properties
```

Create topic:
```bash
kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic {{topic}}
```

List topics:
```bash
kafka-topics --list --bootstrap-server localhost:9092
```

Delete topic:
```bash
kafka-topics --zookeeper localhost:2181 --delete --topic {{topic}}
```

### Consumer