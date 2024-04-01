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

## Best Practices
- **Use User-defined Networks:** Create user-defined networks for isolation and better DNS resolution.

- **Choose the Right Network Driver:** Select from bridge, overlay, or macvlan based on your needs.

- **Implement Network Policies:** Use network policies in swarm mode for security.

- **Minimize Exposed Ports:** Only expose necessary ports to reduce attack surfaces.

- **Prefer Container-to-Container Communication:** Use Docker's internal networking within user-defined networks.

- **Utilize DNS for Communication:** Leverage automatic DNS resolution in user-defined networks for container communication.

- **Use Overlay Networks for Multi-Host:** For multi-host environments, overlay networks facilitate secure and efficient cross-host communication.

- **Monitor Network Traffic:** Implement monitoring and logging for network traffic to detect issues and unauthorized access.

- **Keep Networking Components Updated:** Regularly update Docker and network components for security and performance.

- **Plan for Scalability:** Design your network architecture to easily accommodate growth and changes.
