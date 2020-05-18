# Useful  docker compose commands
    docker-compose start
    docker-compose stop
    docker-compose pause
    docker-compose unpause
    docker-compose ps
    docker-compose up
    # command will start the services on detach mode (similar like running in the background)
    docker-compose up -d
    # Build container	
    docker-compose up -d --build
    docker-compose down
    docker-compose volume
    docker-compose exec ksql-cli 
	docker-compose logs zookeeper | grep -i binding
	docker-compose logs broker | grep -i started
docker-compose exec broker  \
kafka-topics --create --topic foo --partitions 1 --replication-factor 1 --if-not-exists --zookeeper localhost:32181
