# Kafka Python Demo

Orignally for PyCon Fi 2015

## Kafka setup

Start Kafka in a docker container. Using spotify/kafka we get a single
container running zookeeper and a single node of kafka (here we are
running a docker-machine named dev for docker.

```shell
docker run -p 2181:2181 -p 9092:9092 \
  --env ADVERTISED_HOST=`docker-machine ip dev` \
  --env ADVERTISED_PORT=9092 spotify/kafka
```

## Kafka demo

Start the consumer
```shell
export ZOOKEEPER=`docker-machine ip dev`:2181
kafka-console-consumer.sh --zookeeper $ZOOKEEPER --topic test
```

Start the producer:
```shell
export KAFKA=`docker-machine ip dev`:9092
kafka-console-producer.sh --broker-list $KAFKA --topic test
```

Punch keyboard, hit enter!

## Consuming everything in a topic

Start the consumer with --from-beginning
```shell
export ZOOKEEPER=`docker-machine ip dev`:2181
kafka-console-consumer.sh --zookeeper $ZOOKEEPER --topic test \
    --from-beginning
```


## Kafka with Python

First, let's install
[kafka-python](https://kafka-python.readthedocs.org/en/latest/)

```shell
pip install kafka-python
```

Let's try writing a simple producer
```python

kafka = KafkaClient('192.168.99.100:9092')

192.168.99.100
```
