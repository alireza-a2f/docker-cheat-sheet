# Docker Containers Cheat Sheet

## Running Containers

- `docker container run IMAGE [COMMAND] [ARG...]`: Run a container.
    - `-d`: Run the container in detached mode.
    - `--name NAME`: Assign a name to the container.
    - `-p hostPort:containerPort`: Map port from host to container.
    - `-v hostDir:containerDir`: Bind mount a volume.
    - `-e KEY=VALUE`: Set an environment variable.
    - `--rm`: Remove the container when it exits.
    - `-it`: Interactive shell.
    - `--network`: Set the container's network.

## Managing Container Execution

- `docker container ls [OPTIONS]`: List containers.
    - `-a`: Show all containers.
- `docker container stop CONTAINER_ID/NAME`: Stop a container.
- `docker container start CONTAINER_ID/NAME`: Start a container.
- `docker container restart CONTAINER_ID/NAME`: Restart a container.
- `docker container kill CONTAINER_ID/NAME`: Kill a container.
- `docker container rm CONTAINER_ID/NAME`: Remove a container.
    - `-f`: Force removal of a running container.
- `docker container pause CONTAINER_ID/NAME`: Pause processes in a container.
- `docker container unpause CONTAINER_ID/NAME`: Unpause processes in a container.

## Interacting with Containers

- `docker container exec [OPTIONS] CONTAINER COMMAND [ARG...]`: Execute a command in a container.
    - `-it`: Interactive shell.
- `docker container logs CONTAINER_ID/NAME`: Fetch container logs.
- `docker container attach CONTAINER_ID/NAME`: Attach to a container.

## Container Inspection and Management

- `docker container top CONTAINER_ID/NAME [ps OPTIONS]`: Display running processes within a container.
- `docker container inspect CONTAINER_ID/NAME`: Inspect a container.
- `docker container stats [OPTIONS] [CONTAINER...]`: Display container resource usage statistics.
- `docker container rename CURRENT_NAME NEW_NAME`: Rename a container.

## Cleaning Up

- `docker container prune`: Remove all stopped containers.
- `docker system prune`: Remove unused data.

## Saving and Loading Containers

- `docker commit CONTAINER_ID REPOSITORY[:TAG]`: Create an image from a container's changes.
