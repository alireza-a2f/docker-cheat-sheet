# Docker Containers Cheat Sheet

## Running Containers

- **Run a container**: Creates and starts a container from an image.

  ```
  docker run IMAGE [COMMAND] [ARG...]
  ```
    - `-d`: Run the container in detached mode.
    - `--name NAME`: Assign a name to the container.
    - `-p hostPort:containerPort`: Map port from host to container.
    - `-v hostDir:containerDir`: Bind mount a volume.
    - `-e KEY=VALUE`: Set an environment variable.
    - `--rm`: Remove the container when it exits.
    - `-it`: Interactive shell.

## Managing Container Execution

- **List containers**: By default, it shows running containers.
  ```
  docker ps [OPTIONS]
  ```
    - `-a`: Show all containers.
    
- **Stop a container**:
  ```
  docker stop CONTAINER_ID/NAME
  ```
  
- **Start a container**:
  ```
  docker start CONTAINER_ID/NAME
  ```

- **Restart a container**:
  ```
  docker restart CONTAINER_ID/NAME
  ```

- **Kill a container**:
  ```
  docker kill CONTAINER_ID/NAME
  ```

- **Remove a container**:
  ```
  docker rm CONTAINER_ID/NAME
  ```
    - `-f`: Force removal of a running container.

- **Pause/Unpause processes in a container**:
  ```
  docker pause CONTAINER_ID/NAME
  docker unpause CONTAINER_ID/NAME
  ```

## Interacting with Containers

- **Execute a command in a container**:
  ```
  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
  ```
    - `-it`: Interactive shell.

- **Fetch container logs**:
  ```
  docker logs CONTAINER_ID/NAME
  ```

- **Attach to a container**:
  ```
  docker attach CONTAINER_ID/NAME
  ```

## Container Inspection and Management

- **Inspect a container**:
  ```
  docker inspect CONTAINER_ID/NAME
  ```

- **Display container resource usage statistics**:
  ```
  docker stats [OPTIONS] [CONTAINER...]
  ```

- **Rename a container**:
  ```
  docker rename CURRENT_NAME NEW_NAME
  ```

## Volume and Network Management

- **Create a volume**:
  ```
  docker volume create [OPTIONS] [VOLUME]
  ```

- **Create a network**:
  ```
  docker network create [OPTIONS] [NETWORK]
  ```

## Cleaning Up

- **Remove all stopped containers**:
  ```
  docker container prune
  ```

- **Remove unused data**:
  ```
  docker system prune
  ```

## Saving and Loading Containers

- **Create an image from a container's changes**:
  ```
  docker commit CONTAINER_ID REPOSITORY[:TAG]
  ```
