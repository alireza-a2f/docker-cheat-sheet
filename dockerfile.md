# Dockerfile Cheat Sheet

## Basic Instructions

- **FROM**: Initializes a new build stage and sets the Base Image.
  ```Dockerfile
  FROM <image>:<tag>
  ```

- **RUN**: Executes commands in a new layer on top of the current image.
  ```Dockerfile
  RUN <command>
  ```

- **CMD**: Provides defaults for an executing container. Only one CMD allowed.
  ```Dockerfile
  CMD ["executable","param1","param2"]
  ```

- **LABEL**: Adds metadata to an image.
  ```Dockerfile
  LABEL <key>=<value> ...
  ```

- **EXPOSE**: Informs Docker that the container listens on specified network ports.
  ```Dockerfile
  EXPOSE <port>
  ```

- **ENV**: Sets environment variable.
  ```Dockerfile
  ENV <key> <value>
  ```

- **ADD**: Copies new files, directories, or remote file URLs and adds them to the filesystem of the container.
  ```Dockerfile
  ADD <src> <dest>
  ```

- **COPY**: Copies new files or directories and adds them to the filesystem of the container.
  ```Dockerfile
  COPY <src> <dest>
  ```

- **ENTRYPOINT**: Configures a container that will run as an executable.
  ```Dockerfile
  ENTRYPOINT ["executable", "param1", "param2"]
  ```

- **VOLUME**: Creates a mount point and marks it as holding externally mounted volumes.
  ```Dockerfile
  VOLUME ["/data"]
  ```

- **USER**: Sets the username or UID used for running the image.
  ```Dockerfile
  USER <user>[:<group>]
  ```

- **WORKDIR**: Sets the working directory for instructions like RUN, CMD, ENTRYPOINT, COPY, and ADD.
  ```Dockerfile
  WORKDIR /path/to/workdir
  ```

- **ARG**: Defines a variable to pass to Docker at build time.
  ```Dockerfile
  ARG <name>[=<default value>]
  ```

- **ONBUILD**: Adds a trigger instruction to be executed at a later stage when the image is used as a base for another build.
  ```Dockerfile
  ONBUILD <INSTRUCTION>
  ```


### Example Dockerfile for a Django-Vue Project

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
