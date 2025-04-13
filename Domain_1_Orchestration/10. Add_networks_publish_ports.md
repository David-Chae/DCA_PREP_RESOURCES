# Docker Networking and Port Publishing

## Adding Networks in Docker

To create and use a network in Docker, follow these steps:

```sh
# Create a user-defined bridge network
docker network create my_network

# Run a container and connect it to the network
docker run -d --name my_container --network my_network my_image
```

For more details, refer to the [Docker Network Documentation](https://docs.docker.com/network/).

## Publishing Ports in Docker

To expose container ports to the host machine, use the `-p` flag:

```sh
# Publish port 8080 on the host to 80 in the container
docker run -d -p 8080:80 my_image
```

This allows access to the container’s service from `http://localhost:8080`.

For more details, refer to the 

### Official Documentation
- [Docker Ports Documentation](https://docs.docker.com/config/containers/container-networking/).
- [Publish ports](https://docs.docker.com/engine/swarm/services/#publish-ports)
- [Connect the service to an overlay network](https://docs.docker.com/engine/swarm/services/#connect-the-service-to-an-overlay-network)

### Asciinema Examples
- [Add networks, publish ports](https://asciinema.org/a/224818)
