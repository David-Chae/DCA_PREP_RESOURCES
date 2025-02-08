
# Identifying the External IP and Port for a Docker Container

## Introduction

When you run a container in Docker and publish ports, it becomes accessible from outside the container. To identify which IP address and port a container is externally accessible on, you need to inspect the Docker container's port mappings and the host's IP address. This guide explains how to find that information.

## Steps to Identify the External IP and Port

### 1. **Check the Published Ports for Running Containers**

To find which ports a container is accessible on, use the `docker ps` command. This command shows a list of all running containers along with their port mappings.

```bash
docker ps
```

This command will display a list of all running containers and their published ports. The output will look something like this:

```
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                  NAMES
abcd1234efgh   nginx     "/docker-entrypoint.…"   2 minutes ago   Up 1 minute    0.0.0.0:8080->80/tcp   my_nginx
```

In this example:
- The container `my_nginx` is running an `nginx` web server.
- The `PORTS` column shows that port `80` inside the container is mapped to port `8080` on the host (`0.0.0.0:8080->80/tcp`).
  - `0.0.0.0` means it is bound to all IP addresses on the host machine.
  - `8080` is the host port that is exposed to the outside world.

### 2. **Identifying the Host IP Address**

By default, Docker binds the ports to `0.0.0.0` (which means all IP addresses on the host). To determine the external IP of the host machine, use the following commands based on your operating system:

#### On Linux:
You can find the host IP by using `ip` or `ifconfig` commands:

```bash
ip addr show
```

Look for the IP address associated with your network interface (e.g., `eth0` or `wlan0`).

Alternatively:

```bash
ifconfig
```

#### On macOS:
Use the `ifconfig` command:

```bash
ifconfig
```

Look for the IP address associated with `en0` or the network interface you are connected to.

#### On Windows:
Use the `ipconfig` command:

```bash
ipconfig
```

Look for the "IPv4 Address" under your active network connection.

### 3. **Accessing the Container Externally**

Once you know the host IP address and the published port, you can access the container's service externally by navigating to:

```
http://<host_ip>:<host_port>
```

For example, if the Docker host's IP is `192.168.1.100` and the container is exposed on port `8080`, you can access the container at:

```
http://192.168.1.100:8080
```

Alternatively, if you are running the container on your local machine, you can access it using `localhost`:

```
http://localhost:8080
```

### 4. **Inspecting Container Details**

For more detailed information about a container’s port mapping, you can use the `docker inspect` command. This provides a JSON output with detailed networking information.

```bash
docker inspect <container_name_or_id>
```

Look for the `NetworkSettings` section in the output. Specifically, you can check the `Ports` and `IPAddress` fields. For example:

```json
"NetworkSettings": {
  "Ports": {
    "80/tcp": [
      {
        "HostPort": "8080"
      }
    ]
  },
  "IPAddress": "172.17.0.2"
}
```

- `HostPort`: This is the port on the host that is mapped to the container's port.
- `IPAddress`: This is the internal IP address of the container (it may not be relevant for external access unless you're connecting from other containers).

### 5. **Accessing Container Using Host's IP Address**

If you need to access the container from another machine on the network, use the host machine's IP address and the published port. The internal container IP address (`IPAddress`) is generally not used for external access but is useful for inter-container communication.

## Official Documentation

For more information on Docker networking and inspecting containers, refer to the official Docker documentation:

- [Docker Networking Overview](https://docs.docker.com/network/)
- [Docker Inspect Command](https://docs.docker.com/engine/reference/commandline/inspect/)
- [Docker Run Command - Exposing Ports](https://docs.docker.com/engine/reference/run/#publish-or-expose-port)

## Conclusion

By following these steps, you can identify the external IP address and port that a Docker container is accessible on. This allows you to interact with services running inside containers from outside the Docker host. Understanding Docker networking is essential for managing multi-container applications and ensuring proper communication between services.
