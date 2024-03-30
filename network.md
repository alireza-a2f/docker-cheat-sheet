# Docker Network Cheat Sheet

## Network Inspection and Management

- `docker container port CONTAINER_ID/NAME [PRIVATE_PORT]`: List port mappings for a container.
- `docker inspect -f '{{ .NetworkSettings.IPAddress }}' CONTAINER_ID/NAME`: Retrieving container IP address.
- `docker network ls`: List all networks created on the Docker host.
- `docker network inspect NETWORK_ID/NAME`: Inspect a docker network.
- `docker network create [OPTIONS] [NETWORK]`: Create a network.
    - `--driver`: Select network driver.
- `docker network connect NETWORK_ID/NAME CONTAINER_ID/NAME`: Connect a container to a network.
- `docker network disconnect NETWORK_ID/NAME CONTAINER_ID/NAME`: Disconnect a container from a network.
