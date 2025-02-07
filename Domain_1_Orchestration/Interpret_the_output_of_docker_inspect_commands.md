# Interpreting the Output of `docker inspect`

The `docker inspect` command provides detailed information about Docker objects such as containers, images, volumes, networks, and services in **JSON format**. The output can be quite extensive, so understanding its structure is key.

---

## 1. Inspecting Different Docker Objects
You can inspect various Docker objects using:

- **Container:**
  ```sh
  docker inspect <container_id or container_name>
  ```
- **Image:**
  ```sh
  docker inspect <image_id or image_name>
  ```
- **Volume:**
  ```sh
  docker inspect <volume_name>
  ```
- **Network:**
  ```sh
  docker inspect <network_name>
  ```
- **Service (Swarm mode):**
  ```sh
  docker service inspect <service_name>
  ```

---

## 2. Understanding the JSON Output
The output consists of **key-value pairs** structured as an array of JSON objects. Here are key sections and their meanings:

### **A. Container Information**
```json
[
  {
    "Id": "c3c7b1fdfb6a...",
    "Created": "2025-02-08T12:34:56.789Z",
    "State": {
      "Status": "running",
      "Running": true,
      "Paused": false,
      "Restarting": false,
      "OOMKilled": false
    },
    "Config": {
      "Hostname": "my-container",
      "Image": "nginx",
      "Env": [
        "PATH=/usr/local/bin:/usr/bin:/bin"
      ],
      "Cmd": [
        "nginx",
        "-g",
        "daemon off;"
      ]
    },
    "NetworkSettings": {
      "IPAddress": "172.17.0.2",
      "Ports": {
        "80/tcp": [
          {
            "HostIp": "0.0.0.0",
            "HostPort": "8080"
          }
        ]
      }
    }
  }
]
```

**Key Sections:**
- **`Id`** – Unique identifier of the container.
- **`State`** – Shows whether the container is running, paused, or restarting.
- **`Config`** – Contains environment variables (`Env`), hostname, image name, and commands (`Cmd`) used to start the container.
- **`NetworkSettings`** – Displays the IP address and port mappings.

---

### **B. Image Information**
```json
[
  {
    "Id": "sha256:abcd1234...",
    "RepoTags": ["nginx:latest"],
    "Created": "2025-02-08T10:00:00Z",
    "Size": 23456789,
    "Architecture": "amd64",
    "Os": "linux"
  }
]
```
- **`RepoTags`** – Shows the image name and tag.
- **`Size`** – Image size in bytes.
- **`Architecture`** – CPU architecture (e.g., `amd64`, `arm64`).
- **`Os`** – Operating system used in the image.

---

### **C. Network Information**
```json
[
  {
    "Name": "my_network",
    "Id": "2f0a30bc...",
    "Driver": "bridge",
    "Containers": {
      "c3c7b1fdfb6a": {
        "Name": "my-container",
        "IPv4Address": "172.18.0.2/16"
      }
    }
  }
]
```
- **`Name`** – Network name.
- **`Driver`** – Network type (`bridge`, `overlay`, etc.).
- **`Containers`** – Lists connected containers and their IP addresses.

---

## 3. Filtering Output with `--format`
To extract specific details, use `--format` with Go templates:

- Get only the container’s IP address:
  ```sh
  docker inspect --format '{{ .NetworkSettings.IPAddress }}' my-container
  ```
- Get container status:
  ```sh
  docker inspect --format '{{ .State.Status }}' my-container
  ```
- Get the image ID:
  ```sh
  docker inspect --format '{{ .Id }}' nginx:latest
  ```

---

## 4. Relevant Official Documentation
- [Docker Inspect Command](https://docs.docker.com/engine/reference/commandline/inspect/)
- [Inspect a service on the swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/inspect-service/)
- [Understanding Container JSON Output](https://docs.docker.com/engine/api/v1.41/#tag/Container)
- [Docker Networking JSON Fields](https://docs.docker.com/network/)
