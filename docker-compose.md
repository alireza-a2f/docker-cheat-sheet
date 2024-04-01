# Docker Compose Cheat Sheet

## Basic Commands

- `docker-compose up -d`: Start up your services in the background.
- `docker-compose build`: Build or rebuild services specified in the `docker-compose.yml`.
- `docker-compose ls`: List the currently running services.
- `docker-compose stop`: Stop running services without removing them.
- `docker-compose down`: Stop and remove containers, networks, volumes, and images created by `up`.
- `docker-compose logs`: View output from containers.
- `docker-compose exec service_name command`: Run a command in a running container.

## docker-compose.yml Basics

A simple `docker-compose.yml` example for a web application might look like this:

```yaml
version: '3'
services:
  web:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/share/nginx/html
  db:
    image: postgres:13
    environment:
      POSTGRES_PASSWORD: example
```

- **version:** Specifies the Compose file version.
- **services:** Defines the services your application consists of.
  - **image:** Specifies the image to start the container from.
  - **ports:** Maps TCP ports on the container to the host.
  - **volumes:** Mount paths or volumes.
  - **environment:** Add environment variables.

## Advanced Features

- **Volumes:** Define and use volumes for persistent or shared data between services.
  ```yaml
  volumes:
    db_data:
  ```

- **Networks:** Configure networking for your services.
  ```yaml
  networks:
    app_network:
  ```

- **Environment Variables:** Use environment variables in configuration.
  ```yaml
  environment:
    - DEBUG=1
  ```

- **Depends On:** Manage inter-service dependencies.
  ```yaml
  depends_on:
    - db
  ```

- **Build:** Build configuration from a `Dockerfile` rather than using a pre-built image.
  ```yaml
  build: .
  ```

## Best Practices

- **Keep It Simple:** Start with the basics and add more options as needed.

- **Use `.env` Files:** Externalize configuration to environment variables and use a `.env` file for local development.

- **Volumes for Development:** Use volumes to mount source code into the container for live reloading during development.

- **Service Dependencies:** Use `depends_on` to start services in dependency order.

- **Separate Development and Production:** Consider different `docker-compose` files for development, testing, and production environments.
