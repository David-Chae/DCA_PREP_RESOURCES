
# Demonstrating Docker Image Tagging

## Overview

Tagging a Docker image is a way to give an image a human-readable alias. This makes it easier to reference and manage images. Tags typically include a name and an optional version, separated by a colon. 

## Example: Tagging a Docker Image

### Step 1: Pull an Image

First, pull a base image from Docker Hub. For example, we'll pull the latest Ubuntu image:

```bash
docker pull ubuntu:latest
```

### Step 2: Tag the Image

To tag the pulled image with a new tag, use the `docker tag` command followed by the existing image ID or name, and the new tag:

```bash
docker tag ubuntu:latest myrepo/ubuntu:mytag
```

In this example:
- `ubuntu:latest` is the existing image name and tag.
- `myrepo/ubuntu:mytag` is the new tag for the image.

### Step 3: Verify the Tagged Image

To verify that the image has been tagged correctly, list all images:

```bash
docker images
```

You should see the newly tagged image in the list.

### Example Output

```
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              abc123              2 days ago          64MB
myrepo/ubuntu       mytag               abc123              2 days ago          64MB
```

## Suggested Documentation

For more detailed information on tagging Docker images, refer to the following documentation:

- [docker image tag](https://docs.docker.com/reference/cli/docker/image/tag/)


