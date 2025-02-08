
# Pulling a Docker Image from a Registry

## Overview

Pulling a Docker image from a registry allows you to download and use images stored in public or private repositories. This guide provides instructions on how to pull images from Docker Hub and other registries.

## Steps to Pull a Docker Image from a Registry

### Step 1: Open Your Terminal

Open a terminal on your machine where Docker is installed.

### Step 2: Use the `docker pull` Command

Run the `docker pull` command followed by the image name and tag:

```bash
docker pull <image_name>:<tag>
```

For example, to pull the latest Nginx image from Docker Hub, you would run:

```bash
docker pull nginx:latest
```

If you don't specify a tag, Docker will default to the `latest` tag.

```bash
docker pull nginx
```

### Step 3: Pull an Image from a Private Registry

To pull an image from a private registry, include the registry address in the image name:

```bash
docker pull <registry_address>/<image_name>:<tag>
```

For example:

```bash
docker pull myregistry.example.com/myimage:latest
```

### Step 4: Verify the Pulled Image

After pulling the image, verify that it has been downloaded successfully by listing all Docker images:

```bash
docker images
```

You should see the newly pulled image in the list.

### Example Output

```
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
nginx                   latest              abc123              2 days ago          133MB
myregistry.example.com/myimage  latest      def456              5 days ago          200MB
```

## Suggested Documentation

For more detailed information on pulling Docker images from a registry, refer to the following documentation:

- [Docker CLI Reference - pull](https://docs.docker.com/engine/reference/commandline/pull/)
- [Pull from a different registry](https://docs.docker.com/reference/cli/docker/image/pull/#pull-from-a-different-registry)
- [Docker Registry - Overview](https://docs.docker.com/registry/)
- [How to Use Your Own Registry](https://www.docker.com/blog/how-to-use-your-own-registry-2/)
