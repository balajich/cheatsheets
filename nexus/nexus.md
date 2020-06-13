# Starting a nexus repo in docker container

    docker run -d -p 8081:8081 --name nexus sonatype/nexus3

# Stop docker container
    
    docker stop --time=120 <CONTAINER_NAME>
# To Test
    curl http://localhost:8081/

# Using docker-compose
    
