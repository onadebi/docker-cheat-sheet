# docker-cheat-sheet

To filter from list of containers (both running and non-running), use below sample command:
## docker ps --all --filter "name=mariadb"

To filter from docker images, one of several ways is to filter by reference, as shown in the example below:
## docker images --filter=reference='*rabbit*'

> You can check the networks that a Docker container is part of using the docker inspect command. 
Replace container_name_or_id with the name or ID of your Docker container. Here's an example:
```
docker inspect -f '{{range .NetworkSettings.Networks}}{{.NetworkID}}{{end}}' postgreslocal
```

> This command prints the ID of the network to which the container is connected. If you want more detailed information about the networks, you can use:
```
docker inspect container_name_or_id
```

> If you want a more user-friendly view of the networks a container is part of, you can use the following command:
```
docker network inspect $(docker inspect -f '{{range .NetworkSettings.Networks}}{{.NetworkID}}{{end}}' container_name_or_id)
```
This command provides detailed information about the network, including its name, ID, and the containers connected to it.

> To add a container to another network in Docker, you can use the docker network connect command. Here's an example:
```
docker network connect network_name container_name_or_id
```
Example: <b style='font-style:italic;color:green;font-weight:bold;'>docker network connect my-network postgreslocal</b>

Keep in mind that a container can be connected to multiple networks simultaneously. If you want to disconnect a container from a network, you can use the  `docker network disconnect` command:
```
docker network disconnect network_name container_name_or_id
```
Example: `docker network disconnect my-network postgreslocal` This command disconnects the postgreslocal container from the my-network network.
