# Useful  docker  commands
    # Remove all stopped docker containters
    docker rm $(docker ps -a -q)
    # To delete unused volumes 
    docker volume rm $(docker volume ls -q --filter dangling=true)