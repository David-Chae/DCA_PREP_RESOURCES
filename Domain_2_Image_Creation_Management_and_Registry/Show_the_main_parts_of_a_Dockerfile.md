# Show the main parts of a Dockerfile

---

## Dockerfile Reference

A **Dockerfile** is a text document that contains all the commands a user could call on the command line to assemble an image. It supports various instructions:

## Main Instructions

### FROM
Specifies the base image for the Docker image you are building. It is typically the first instruction in a Dockerfile.

```dockerfile
FROM ubuntu:latest
```

### RUN
Executes commands in a new layer. It is commonly used to install packages and configure the environment.

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
Specifies the default command to run when the container starts. It can be overridden by passing a command to `docker run`.

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
Indicates which ports the container listens on.

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

### ONBUILD
Adds instructions to be executed when the image is used as the base for another build.

```dockerfile
ONBUILD RUN apt-get update && apt-get install -y python
```

### SHELL
Sets the default shell used for the shell form of commands.

```dockerfile
SHELL ["/bin/bash", "-c"]
```

### STOPSIGNAL
Specifies the system call signal that will be sent to the container to exit.

```dockerfile
STOPSIGNAL SIGKILL
```

## Parser Directives

Parser directives are special instructions that affect how the Dockerfile is processed. They must appear at the very top of the Dockerfile and begin with the `#` symbol.

### Syntax Directive
Specifies the Dockerfile syntax version or an alternative parser.

```dockerfile
# syntax=docker/dockerfile:1.3
```

### Escape Directive
Sets the character used to escape newline characters in the Dockerfile.

```dockerfile
# escape=`
```

## Environment Replacement

Docker supports the use of environment variables in Dockerfile instructions. These variables can be set using the `ENV` instruction and used with `${variable_name}` syntax.

```dockerfile
ENV BASE_URL=https://example.com
ADD ${BASE_URL}/file.tar.gz /app/
```

## .dockerignore File

The `.dockerignore` file works similarly to `.gitignore`. It allows you to exclude files and directories from the context when building a Docker image.

Example `.dockerignore` file:

```
node_modules
*.log
```

## Shell and Exec Form

Dockerfile instructions like `RUN`, `CMD`, and `ENTRYPOINT` can use either shell form or exec form.

### Shell Form
Uses the default shell to run commands.

```dockerfile
RUN apt-get update && apt-get install -y nginx
```

### Exec Form
Provides a JSON array with the command and its arguments, bypassing the shell.

```dockerfile
RUN ["apt-get", "update"]
RUN ["apt-get", "install", "-y", "nginx"]
```

## Suggested Documentation

For more detailed information on Dockerfile options, refer to the following documentation:

- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
- [Best Practices for Writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Docker Official Images](https://docs.docker.com/docker-hub/official_images/)

These resources provide comprehensive insights into Dockerfile options, best practices, and examples to help you create efficient and effective Docker images.
