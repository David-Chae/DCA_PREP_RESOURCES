
# Configuring L7 Load Balancing with Docker EE
Describe and demonstrate how to use Docker to load balance HTTP/HTTPs traffic to an application (Configure L7 load balancing with Docker EE).

## Introduction

Layer 7 (L7) load balancing refers to the application layer of the OSI model and is typically used for routing HTTP/HTTPS traffic based on the content of the requests (e.g., URL paths, headers, etc.). Docker Enterprise Edition (Docker EE) offers a powerful, built-in solution for load balancing through its routing mesh in Docker Swarm mode.

In this guide, we will demonstrate how to configure Docker to load balance HTTP/HTTPS traffic to an application using Docker EE and the Docker Swarm routing mesh.

## Prerequisites

- Docker EE installed and configured on a Swarm cluster.
- A Docker Swarm mode cluster with at least two nodes.
- A basic understanding of Docker services and Docker Compose.
- A running application (e.g., a simple web application using Nginx or Apache) that can accept HTTP/HTTPS traffic.

## Steps to Configure L7 Load Balancing in Docker EE

### 1. **Initialize Docker Swarm Mode**

If your Docker environment is not yet initialized in Swarm mode, start by initializing it:

```bash
docker swarm init
```

This command will initialize Swarm mode and allow the manager node to control the cluster.

### 2. **Deploy the Application in Docker Swarm**

To enable load balancing, you need to deploy your application as a Docker service. In this example, we'll use a simple Nginx web application.

Create a `docker-compose.yml` file for your application. Here is an example configuration for deploying two replicas of an Nginx service:

```yaml
version: '3.7'

services:
  web:
    image: nginx
    deploy:
      replicas: 3
      labels:
        - "traefik.enable=true"
    ports:
      - "80:80"
      - "443:443"
```

In this example:

- The `web` service is deployed with 3 replicas of Nginx.
- Ports `80` and `443` are exposed for HTTP and HTTPS traffic, respectively.
- We use a `deploy` section to define the number of replicas and enable load balancing across the nodes.

### 3. **Configure HTTP/HTTPS Load Balancing**

To set up HTTP/HTTPS load balancing, Docker uses a routing mesh. When a request hits any node in the Swarm cluster, it is routed to an available container, even if the container is not running on the node that received the request.

Now, create a load balancer using a reverse proxy, such as **Traefik** or **NGINX**, that will handle the HTTP/HTTPS traffic and distribute it to the application services.

#### Example with Traefik

Create a `docker-compose.yml` file for deploying Traefik as the reverse proxy. This configuration will enable HTTP/HTTPS routing based on URL path and forward the traffic to the application containers.

```yaml
version: '3.7'

services:
  reverse-proxy:
    image: traefik:v2.5
    command:
      - "--api.insecure=true"
      - "--providers.docker=true"
    ports:
      - "80:80"   # HTTP
      - "443:443"  # HTTPS
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"

  web:
    image: nginx
    deploy:
      replicas: 3
      labels:
        - "traefik.http.routers.web.rule=Path(`/`)"
        - "traefik.http.services.web.loadbalancer.server.port=80"
```

In this example:

- The **Traefik** service is configured to expose HTTP and HTTPS ports (`80` and `443`).
- Traefik will automatically detect the **web** service containers and route the HTTP/HTTPS traffic to them based on the URL path rule (`Path(`/`)`).

### 4. **Deploy the Services to Docker Swarm**

Deploy the services to the Docker Swarm cluster using `docker stack deploy`. Make sure to run this command on the manager node:

```bash
docker stack deploy -c docker-compose.yml myapp
```

This will create the application stack with the reverse proxy and application services.

### 5. **Testing the Load Balancer**

Once the services are deployed, the Traefik reverse proxy will automatically route traffic to the available application replicas. You can test the load balancing by sending HTTP/HTTPS requests to any of the Swarm nodes' IP addresses.

```bash
curl http://<swarm_node_ip>
curl https://<swarm_node_ip> --insecure
```

You should see the Nginx welcome page (or the default application response) being served by the container. Traefik will distribute the load across the available replicas of the `web` service.

### 6. **Scaling the Application**

To scale the application by adding more replicas, use the following command:

```bash
docker service scale myapp_web=5
```

This will increase the number of replicas to 5, and Traefik will continue to balance the traffic across all available replicas.

## Official Documentation

For more information on configuring Docker EE, load balancing, and using Traefik with Docker, refer to the following official documentation:

- [Docker Swarm Mode Overview](https://docs.docker.com/engine/swarm/)
- [Docker Compose File Reference](https://docs.docker.com/compose/compose-file/)
- [Traefik with Docker](https://doc.traefik.io/traefik/providers/docker/)
- [Docker EE Networking](https://docs.docker.com/engine/swarm/networking/)
- [Docker Service and Load Balancing](https://docs.docker.com/engine/swarm/services/#published-ports)

## Conclusion
By using Docker Swarm's built-in routing mesh and a reverse proxy like Traefik, you can easily set up Layer 7 (L7) load balancing for HTTP/HTTPS traffic. This allows for scalable and resilient applications with automatic traffic distribution, making it ideal for both production and development environments.
