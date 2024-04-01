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

## Best Practices

- **Use Official Images:** Prefer official Docker images as a base for reliability and security.

- **Keep Containers Immutable:** Avoid making changes to running containers. Rebuild and redeploy containers for updates.

- **Use Specific Image Tags:** Specify exact image versions to ensure consistency and avoid unexpected changes.

- **Minimize Container Footprint:** Use minimal base images like Alpine for smaller, more secure containers.

- **Limit Container Responsibilities:** Follow the one-process-per-container principle for isolation and scalability.

- **Manage Secrets Securely:** Use Docker secrets or external secrets management tools instead of hardcoding in images.

- **Set Resource Limits:** Apply CPU and memory limits to containers to prevent resource hogging (`--cpus`, `--memory`).

- **Log to STDOUT/STDERR:** Configure applications to write logs to console, enabling Docker to manage logs effectively.

- **Keep Containers Stateless:** Design for statelessness to facilitate scalability, easy updates, and high availability.

- **Secure Containers:** Run as a non-root user, remove unnecessary privileges, and use read-only filesystems where possible.

- **Monitor Container Health:** Utilize `HEALTHCHECK` instructions in Dockerfiles or container orchestration health checks.

- **Network Security:** Utilize user-defined networks for isolation and apply firewall rules for external communications.

- **Regularly Update Images:** Keep images updated with the latest patches for security and performance.

- **Prune Unused Objects:** Regularly clean up unused images, containers, networks, and volumes to free up space.

- **Use Docker Compose for Development:** Leverage Docker Compose to define and run multi-container applications during development.
