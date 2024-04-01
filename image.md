# Docker Images Cheat Sheet

## Image Inspection and Management

- `docker image ls`: List all local images.
- `docker image pull [IMAGE_NAME]:[TAG]`: Download an image from Docker Hub.
- `docker image build -t [YOUR_IMAGE_NAME]:[TAG] .`: Build an image from a Dockerfile in the current directory.
- `docker image tag [SOURCE_IMAGE]:[TAG] [TARGET_IMAGE]:[TAG]`: Tag an image with a new name and/or tag.
- `docker image push [IMAGE_NAME]:[TAG]`: Push an image to Docker Hub or another registry.
- `docker image rm [IMAGE_NAME]:[TAG]`: Remove an image from the local storage.
- `docker image inspect [IMAGE_NAME]:[TAG]`: Inspect an image.

## Best Practices

- **Base Image Selection:**
  - Use **official images** as your base image for reliability and security.
  - Prefer **minimal base images** (like Alpine) to reduce attack surface and image size.

- **Image Building:**
  - **Specify a version tag** in the base image to ensure reproducibility.
  - **Minimize the number of layers** by combining commands (`RUN`, `COPY`, `ADD`) where possible.
  - Use **multi-stage builds** to reduce final image size, by separating build-time dependencies from runtime necessities.

- **Security Practices:**
  - **Scan images for vulnerabilities** with tools like Trivy or Docker Scan.
  - **Avoid running as root**; create a user with less privileges.
  - Implement **health checks** with `HEALTHCHECK` to automate container health monitoring.

- **Efficiency and Caching:**
  - **Leverage Docker's build cache** by organizing Dockerfile instructions from the less frequently changed to the more frequently changed.
  - **Clean up** in the same layer where you install packages or download temporary files to avoid bloating the image.

- **Configuration and Secrets:**
  - **Externalize configuration** from images. Use environment variables for configuration that changes between environments.
  - **Do not store secrets** in Docker images. Use Docker Secrets, environment variables injected at runtime, or external secrets management tools.

- **Image Size Optimization:**
  - **Clean up unnecessary files** and cache from the image in the same layer where they are created.
  - **Use `.dockerignore`** to exclude files and directories that are not needed for the build (e.g., local database files, `node_modules` directory, etc.).

- **Maintainability:**
  - **Document your Dockerfile.** Use comments to explain why certain instructions are included.
  - **Keep your images up-to-date** with the latest patches by regularly rebuilding them.

- **Registry Practices:**
  - **Use tags for versioning** your images and push them to a registry.
  - **Implement a naming convention** for images and tags to help manage versions and environments (e.g., `app:1.2.3`, `app:latest`, `app:staging`).

- **Testing and Quality Assurance:**
  - **Test your images** as part of your CI/CD pipeline. Ensure your containerized application starts correctly and passes all health checks and tests.
