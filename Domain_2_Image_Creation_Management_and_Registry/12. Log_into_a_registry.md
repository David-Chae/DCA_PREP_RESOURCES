
# Logging into a Docker Registry

## Overview

Logging into a Docker registry allows you to access private repositories and manage your Docker images. This guide provides instructions on how to log into both public and private registries.

## Steps to Log into a Docker Registry

### Step 1: Open Your Terminal

Open a terminal on your machine where Docker is installed.

### Step 2: Use the `docker login` Command

Run the `docker login` command followed by the registry's address:

```bash
docker login <registry_address>
```

For example, to log into Docker Hub, you would use:

```bash
docker login
```

To log into a private registry, specify the registry's address:

```bash
docker login registry.example.com
```

### Step 3: Enter Your Credentials

When prompted, enter your username and password:

```bash
Username: <your_username>
Password: <your_password>
```

### Step 4: Verify the Login

After logging in, you can verify that your credentials have been stored by checking the `~/.docker/config.json` file:

```bash
cat ~/.docker/config.json
```

You should see your credentials stored in the file.

## Suggested Documentation

For more detailed information on logging into Docker registries, refer to the following documentation:

- [Docker CLI Reference - login](https://docs.docker.com/reference/cli/docker/login/)
- [How to Login to Docker Hub and Private Registries With The Docker CLI](https://www.howtogeek.com/devops/how-to-login-to-docker-hub-and-private-registries-with-the-docker-cli/)
- [How to login Docker registry | LabEx](https://labex.io/tutorials/docker-how-to-login-docker-registry-418063)


