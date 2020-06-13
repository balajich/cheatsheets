# MySql docker

# Start Server
    docker-compose up -d
# Connect using MySQL client
    docker-compose exec mysqldb mysql --user=alex --password=alexpass
# Stop and delete container 
    docker-compose down -v