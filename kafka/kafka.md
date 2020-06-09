#Start Cluster
    # on branch origin/5.5.0-post
    git status
    sudo sysctl -w vm.max_map_count=262144
    sysctl -a | grep max_map_count
    cd ./cp-all-in-one/cp-all-in-one
    docker-compose up -d --build
    docker-compose ps
    docker-compose down -v
# UI
    http://localhost:9021/clusters
# topics commands

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

# Kafka Rest proxy
    # Create a topic jsontest
    curl -X POST -H "Content-Type: application/vnd.kafka.json.v2+json" \
          -H "Accept: application/vnd.kafka.v2+json" \
          --data '{"records":[{"value":{"foo":"bar"}}]}' "http://localhost:8082/topics/jsontest"
   
    # Create a consumer group my_consumer_instance
    curl -X POST -H "Content-Type: application/vnd.kafka.v2+json" \
      --data '{"name": "my_consumer_instance", "format": "json", "auto.offset.reset": "earliest"}' \
      http://localhost:8082/consumers/my_json_consumer
    
    # subscribe to consumer group
    curl -X POST -H "Content-Type: application/vnd.kafka.v2+json" --data '{"topics":["jsontest"]}' \
    http://localhost:8082/consumers/my_json_consumer/instances/my_consumer_instance/subscription
    
    # Get records from json topic
    curl -X GET -H "Accept: application/vnd.kafka.json.v2+json" \
      http://localhost:8082/consumers/my_json_consumer/instances/my_consumer_instance/records
    
    # Delete consumer instance
    curl -X DELETE \
      http://localhost:8082/consumers/my_avro_consumer/instances/my_consumer_instance

# References
- https://docs.confluent.io/current/quickstart/ce-docker-quickstart.html
# Rest proxy postman file
Kafka-Rest-Proxy.postman_collection.json