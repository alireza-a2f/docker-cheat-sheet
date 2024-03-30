# Docker Images Cheat Sheet

## Image Inspection and Management

- `docker image ls`: List all local images.
- `docker image pull [IMAGE_NAME]:[TAG]`: Download an image from Docker Hub.
- `docker image build -t [YOUR_IMAGE_NAME]:[TAG] .`: Build an image from a Dockerfile in the current directory.
- `docker image tag [SOURCE_IMAGE]:[TAG] [TARGET_IMAGE]:[TAG]`: Tag an image with a new name and/or tag.
- `docker image push [IMAGE_NAME]:[TAG]`: Push an image to Docker Hub or another registry.
- `docker image rm [IMAGE_NAME]:[TAG]`: Remove an image from the local storage.
- `docker image inspect [IMAGE_NAME]:[TAG]`: Inspect an image.
