# Dockerfile Cheat Sheet

## Basic Instructions

- `FROM <image>:<tag>`: Initializes a new build stage and sets the Base Image.
- `RUN <command>`: Executes commands in a new layer on top of the current image.
- `CMD ["executable","param1","param2"]`: Provides defaults for an executing container. Only one CMD allowed.
- `LABEL <key>=<value> ...`: Adds metadata to an image.
- `EXPOSE <port>`: Informs Docker that the container listens on specified network ports.
- `ENV <key> <value>`: Sets environment variable.
- `ADD <src> <dest>`: Copies new files, directories, or remote file URLs and adds them to the filesystem of the container.
- `COPY <src> <dest>`: Copies new files or directories and adds them to the filesystem of the container.
- `ENTRYPOINT ["executable", "param1", "param2"]`: Configures a container that will run as an executable.
- `VOLUME ["/data"]`: Creates a mount point and marks it as holding externally mounted volumes.
- `USER <user>[:<group>]`: Sets the username or UID used for running the image.
- `WORKDIR /path/to/workdir`: Sets the working directory for instructions like RUN, CMD, ENTRYPOINT, COPY, and ADD.
- `ARG <name>[=<default value>]`: Defines a variable to pass to Docker at build time.
- `ONBUILD <INSTRUCTION>`: Adds a trigger instruction to be executed at a later stage when the image is used as a base for another build.

## Best Practices

- **Minimize Layers**: Combine RUN commands with &&.

- **Use .dockerignore**: To exclude unnecessary files from the build context.

- **Prefer COPY Over ADD**: Unless you need tar extraction or remote URLs.

- **Explicit Tags**: Use specific image tags to ensure reproducibility.


## Example Dockerfile for a Django-Vue Project

This example illustrates a multi-stage build Dockerfile for a project with a Django backend and a Vue.js frontend. It compiles the Vue.js frontend app and serves it with an Nginx server, while the Django backend runs in a separate container.

```Dockerfile
# Stage 1: Build the Vue.js front-end
FROM node:14 AS vue_builder
WORKDIR /app
COPY front-end/ ./  # Assume your Vue.js project is in the front-end directory
RUN npm install && npm run build

# Stage 2: Serve the front-end with Nginx
FROM nginx:alpine AS front_end_server
COPY --from=vue_builder /app/dist /usr/share/nginx/html
EXPOSE 80

# Stage 3: Set up the Django back-end
FROM python:3.8 AS django_backend
ENV PYTHONUNBUFFERED 1
WORKDIR /backend
COPY back-end/ ./  # Assume your Django project is in the back-end directory
RUN pip install -r requirements.txt
EXPOSE 8000
CMD ["gunicorn", "-b", "0.0.0.0:8000", "myproject.wsgi:application"]
```
