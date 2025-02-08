# Dockerfile Options

## Overview

A Dockerfile is a text document that contains instructions for building a Docker image. It uses a simple, descriptive syntax to automate the process of configuring and setting up the environment for your applications. Here are some of the most commonly used Dockerfile options:

### FROM

Specifies the base image for the Docker image you are building. It is typically the first instruction in a Dockerfile.

```dockerfile
FROM ubuntu:latest
```

### RUN
Executes a command in the shell. It is commonly used to install packages and configure the environment.

```dockerfile
RUN apt-get update && apt-get install -y nginx
```

### COPY
Copies files or directories from the host system to the Docker image.

```dockerfile
COPY . /app
```

### ADD
Similar to COPY, but also supports fetching files from remote URLs and extracting compressed files.

```dockerfile
ADD https://example.com/file.tar.gz /app/
```

### CMD
Specifies the default command to run when the container starts. It can be overridden by passing a command to docker run.

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

### ENTRYPOINT
Sets the default executable for the container. It is often used in combination with CMD.

```dockerfile
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
```

### ENV
Sets environment variables.

```dockerfile
ENV MY_ENV_VAR=my_value
```

### EXPOSE
Indicates the ports on which the container will listen for connections.

```dockerfile
EXPOSE 80
```

### WORKDIR
Sets the working directory for subsequent instructions.

```dockerfile
WORKDIR /app
```

### VOLUME
Creates a mount point and marks it as holding externally mounted volumes from the host or other containers.

```dockerfile
VOLUME ["/data"]
```

### USER
Sets the user to use when running the image.

```dockerfile
USER appuser
```

### LABEL
Adds metadata to the image in the form of key-value pairs.

```dockerfile
LABEL version="1.0" description="My Docker Image"
```

### HEALTHCHECK
Specifies a command to check the health of the container.

```dockerfile
HEALTHCHECK CMD curl --fail http://localhost:80 || exit 1
```

## Suggested Documentation
For more detailed information on Dockerfile options, refer to the following documentation:

- [Dockerfile Reference](https://docs.docker.com/reference/dockerfile/)
- [Best Practices for Writing Dockerfiles](https://docs.docker.com/build/building/best-practices/)
- [Docker Official Images](https://docs.docker.com/docker-hub/repos/manage/trusted-content/official-images/)

These resources provide comprehensive insights into Dockerfile options, best practices, and examples to help you create efficient and effective Docker images.
