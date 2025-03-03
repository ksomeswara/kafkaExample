docker network create kafka-network

docker run -d --name zookeeper --network kafka-network -p 2181:2181 zookeeper

docker run -d --name kafka -p 9092:9092 \
-e KAFKA_ZOOKEEPER_CONNECT=localhost:2181 \
-e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9092 \
-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092 \
wurstmeister/kafka



docker exec -it kafka kafka-topics.sh \
--create --topic test_topic \
--bootstrap-server localhost:9092 \
--partitions 1 \
--replication-factor 1


docker exec -it kafka kafka-topics.sh \
--create --topic test_topic \
--bootstrap-server localhost:9092 \
--partitions 1 \
--replication-factor 1
