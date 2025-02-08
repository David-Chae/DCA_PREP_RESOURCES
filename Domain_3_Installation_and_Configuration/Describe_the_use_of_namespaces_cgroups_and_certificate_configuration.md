# Docker Security: Namespaces, cgroups, and Certificate Configuration

## Overview
Docker ensures secure and efficient containerized environments using key Linux kernel features such as namespaces and cgroups, along with certificate-based authentication for secure communications.

## 1. Namespaces in Docker
Namespaces provide isolation at the process level, ensuring that containers operate independently.

### Types of Namespaces Used in Docker:
- **PID Namespace**: Isolates process IDs between containers.
- **Network Namespace**: Provides separate networking stacks for containers.
- **Mount Namespace**: Ensures independent file system views.
- **IPC Namespace**: Isolates inter-process communication mechanisms.
- **User Namespace**: Maps user IDs between host and containers for privilege management.

### Checking Namespaces:
```sh
lsns
```

## 2. Control Groups (cgroups)
Cgroups regulate resource allocation to prevent a single container from overusing system resources.

### Key Features:
- **CPU Limiting**: Restrict CPU shares per container.
- **Memory Control**: Prevents excessive RAM usage.
- **I/O Bandwidth**: Controls disk and network bandwidth allocation.

### Configuring cgroups:
```sh
docker run --memory=512m --cpus=1 my_container
```

## 3. Certificate-Based Authentication
Certificate-based authentication ensures secure communication between a Docker daemon and a private registry.

### Step 1: Generate a Certificate Authority (CA)
```sh
mkdir -p ~/certs && cd ~/certs
openssl genrsa -aes256 -out ca-key.pem 4096
openssl req -new -x509 -days 365 -key ca-key.pem -sha256 -out ca.pem
```

### Step 2: Generate Server Certificates
```sh
openssl genrsa -out server-key.pem 4096
openssl req -new -key server-key.pem -out server.csr
openssl x509 -req -days 365 -sha256 -in server.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem
```

### Step 3: Configure Docker Daemon with Certificates
1. Place certificates in `/etc/docker/certs.d/<registry-hostname>/`:
```sh
sudo mkdir -p /etc/docker/certs.d/<registry-hostname>/
sudo cp ca.pem /etc/docker/certs.d/<registry-hostname>/
```
2. Restart Docker daemon:
```sh
sudo systemctl restart docker
```

### Step 4: Configure Docker Client
1. Place client certificates in `~/.docker/`:
```sh
mkdir -p ~/.docker/
mv client-cert.pem ~/.docker/cert.pem
mv client-key.pem ~/.docker/key.pem
mv ca.pem ~/.docker/ca.pem
```
2. Verify secure connection:
```sh
docker --tlsverify --tlscacert=~/.docker/ca.pem \
       --tlscert=~/.docker/cert.pem --tlskey=~/.docker/key.pem \
       -H=<registry-hostname>:2376 info
```

## 4. Documentation Links
- [Docker Namespaces](https://docs.docker.com/engine/security/userns-remap/)
- [Docker cgroups](https://docs.docker.com/config/containers/resource_constraints/)
- [Docker TLS Authentication](https://docs.docker.com/engine/security/https/)
- [Using Secure Docker Registry](https://docs.docker.com/registry/deploying/)

## Conclusion
Namespaces provide isolation, cgroups control resource usage, and certificate-based authentication secures communication. Understanding these components is crucial for managing Docker securely and efficiently.

