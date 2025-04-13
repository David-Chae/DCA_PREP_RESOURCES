# Using Templates with Docker Service Create

## Overview

Docker service templates allow you to dynamically configure service attributes at runtime, providing greater flexibility and control over how your services are deployed. Templates can be used to set environment variables, labels, and other configurations based on the state of the service or the Docker node.

## Example Usage

Below is an example of how to use templates with the `docker service create` command. In this example, we'll create a Docker service that uses a template to set an environment variable based on the service name.

```bash
docker service create \
  --name my_service \
  --env MY_ENV_VAR="{{.Service.Name}}" \
  nginx:latest
```

In this example:
- --name my_service: Sets the name of the service to my_service.
- --env MY_ENV_VAR="{{.Service.Name}}": Sets the environment variable MY_ENV_VAR to the name of the service (my_service). The template {{.Service.Name}} is evaluated at runtime to get the service name.

## Templates in Docker Compose
Templates can also be used in Docker Compose files. Below is an example of a Docker Compose file that uses a template to set a label based on the service name:

```yaml
version: '3.8'

services:
  web:
    image: nginx:latest
    deploy:
      labels:
        - "com.example.service.name={{.Service.Name}}"
```

In this example, the label com.example.service.name is dynamically set to the service name using the template {{.Service.Name}}.

## Suggested Documentation
For more detailed information on using templates with Docker services, refer to the following documentation:

- [Docker Service Create](https://docs.docker.com/reference/cli/docker/service/create/)
- [Service Templates](https://docs.docker.com/engine/swarm/services/#service-templates)
- [Docker Compose File Reference](https://docs.docker.com/reference/compose-file/legacy-versions/)
- [Using Environment Variables in Compose](https://docs.docker.com/compose/how-tos/environment-variables/)

These resources provide comprehensive insights into using templates and other features to enhance your Docker service deployments.
