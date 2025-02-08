
# Deploying a Docker Registry

## Overview

A Docker registry is a storage and distribution system for Docker images. Deploying your own registry allows you to manage and share images within your organization or network, providing better control and security.

## Steps to Deploy a Docker Registry

### Step 1: Install Docker

Ensure Docker is installed on your machine. Follow the official Docker documentation for installation instructions:

- [Install Docker](https://docs.docker.com/engine/install/)

### Step 2: Run the Docker Registry Container

Use the official Docker Registry image to run a registry container. Execute the following command to start the registry:

```bash
docker run -d -p 5000:5000 --name registry registry:2
```

In this example:
- `-d` runs the container in detached mode.
- `-p 5000:5000` publishes port 5000 on your local machine’s network.
- `--name registry` gives the container a name.

### Step 3: Verify the Registry Container

Check the status of the registry container to ensure it is running:

```bash
docker ps
```

You should see the registry container listed with the name `registry`.

### Step 4: Push and Pull Images

To use the registry, you need to push and pull images using the registry’s address. Tag an image with the registry’s address and push it:

```bash
docker tag myimage:latest localhost:5000/myimage:latest
docker push localhost:5000/myimage:latest
```

To pull the image from the registry:

```bash
docker pull localhost:5000/myimage:latest
```

### Step 5: Secure the Registry (Optional)

For production environments, consider securing the registry with TLS and authentication. Refer to the official Docker documentation for detailed instructions:

- [Securing Docker with TLS](https://docs.docker.com/engine/security/https/)
- [Docker Registry Authentication](https://docs.docker.com/registry/deploying/)

## Suggested Documentation

For more detailed information on deploying and managing Docker registries, refer to the following documentation:

- [Deploy a registry server](https://distribution.github.io/distribution/about/deploying/)
- [How to Use Your Own Registry](https://www.docker.com/blog/how-to-use-your-own-registry-2/)
- [Creating a Local Docker Registry: Complete Installation Guide](https://k21academy.com/docker-kubernetes/how-to-set-up-your-own-local-docker-registry-a-step-by-step-guide/)
- [How To Set Up a Private Docker Registry on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-ubuntu-20-04)
