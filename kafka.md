#

    # create a topic
    docker-compose exec broker \
    kafka-topics --create --topic foo --partitions 1 --replication-factor 1 --if-not-exists --zookeeper zookeeper:2181
    
    # Describe a topic
    docker-compose exec broker \
    kafka-topics --describe --topic foo --zookeeper zookeeper:2181
    
    # publish some data to your new topic:
    docker-compose exec broker \
    bash -c "seq 42 | kafka-console-producer --request-required-acks 1 --broker-list broker:9092 --topic foo && echo 'Produced 42 messages.'"
    
    # read back the message using the built-in Console consumer    
    docker-compose exec broker \
    kafka-console-consumer --bootstrap-server broker:9092 --topic foo --from-beginning --max-messages 42