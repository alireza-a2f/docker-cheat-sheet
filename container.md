# Docker Containers Cheat Sheet

## Running Containers

- **Run a container**: `docker container run IMAGE [COMMAND] [ARG...]`
    - `-d`: Run the container in detached mode.
    - `--name NAME`: Assign a name to the container.
    - `-p hostPort:containerPort`: Map port from host to container.
    - `-v hostDir:containerDir`: Bind mount a volume.
    - `-e KEY=VALUE`: Set an environment variable.
    - `--rm`: Remove the container when it exits.
    - `-it`: Interactive shell.
    - `--network`: Set the container's network.

## Managing Container Execution

- **List containers**: `docker container ls [OPTIONS]`
    - `-a`: Show all containers.
    
- **Stop a container**: `docker container stop CONTAINER_ID/NAME`
  
- **Start a container**: `docker container start CONTAINER_ID/NAME`

- **Restart a container**: `docker container restart CONTAINER_ID/NAME`

- **Kill a container**: `docker container kill CONTAINER_ID/NAME`

- **Remove a container**: `docker container rm CONTAINER_ID/NAME`
    - `-f`: Force removal of a running container.

- **Pause processes in a container**: `docker container pause CONTAINER_ID/NAME`

- **Unpause processes in a container**: `docker container unpause CONTAINER_ID/NAME`

## Interacting with Containers

- **Execute a command in a container**: `docker container exec [OPTIONS] CONTAINER COMMAND [ARG...]`
    - `-it`: Interactive shell.

- **Fetch container logs**: `docker container logs CONTAINER_ID/NAME`

- **Attach to a container**: `docker container attach CONTAINER_ID/NAME`

## Container Inspection and Management

- **Display running processes within a container**: `docker container top CONTAINER_ID/NAME [ps OPTIONS]`

- **Inspect a container**: `docker container inspect CONTAINER_ID/NAME`

- **Display container resource usage statistics**: `docker container stats [OPTIONS] [CONTAINER...]`

- **Rename a container**: `docker container rename CURRENT_NAME NEW_NAME`

## Network Management

- **List port mappings for a container**: `docker container port CONTAINER_ID/NAME [PRIVATE_PORT]`

- **Retrieving container IP address**: `docker inspect -f '{{ .NetworkSettings.IPAddress }}' CONTAINER_ID/NAME`

- **List all networks created on the Docker host**: `docker network ls`

- **Show detailed information on a network**: `docker network inspect NETWORK_ID/NAME`

- **Create a network**: `docker network create [OPTIONS] [NETWORK]`
    - `--driver`: Select network driver.

- **Connect a container to a network**: `docker network connect NETWORK_ID/NAME CONTAINER_ID/NAME`

- **Disconnect a container from a network**: `docker network disconnect NETWORK_ID/NAME CONTAINER_ID/NAME`

## Cleaning Up

- **Remove all stopped containers**: `docker container prune`

- **Remove unused data**: `docker system prune`

## Saving and Loading Containers

- **Create an image from a container's changes**: `docker commit CONTAINER_ID REPOSITORY[:TAG]`
