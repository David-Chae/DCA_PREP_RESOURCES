# Certificate-Based Client-Server Authentication in Docker

## Overview
Certificate-based authentication in Docker ensures secure communication between a Docker daemon and a private registry. This setup involves generating TLS certificates for both the client and server, enforcing authentication and encryption.

## 1. Generate Certificates

### Step 1: Create a Certificate Authority (CA)
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

### Step 3: Generate Client Certificates
```sh
openssl genrsa -out client-key.pem 4096
openssl req -new -key client-key.pem -out client.csr
openssl x509 -req -days 365 -sha256 -in client.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out client-cert.pem
```

## 2. Configure Docker Daemon
1. Place certificates in `/etc/docker/certs.d/<registry-hostname>/`:
```sh
sudo mkdir -p /etc/docker/certs.d/<registry-hostname>/
sudo cp ca.pem /etc/docker/certs.d/<registry-hostname>/
```
2. Restart Docker daemon:
```sh
sudo systemctl restart docker
```

## 3. Configure the Docker Client
1. Place client certificates in `~/.docker/`:
```sh
mkdir -p ~/.docker/
mv client-cert.pem ~/.docker/cert.pem
mv client-key.pem ~/.docker/key.pem
mv ca.pem ~/.docker/ca.pem
```
2. Test secure connection:
```sh
docker --tlsverify --tlscacert=~/.docker/ca.pem \
       --tlscert=~/.docker/cert.pem --tlskey=~/.docker/key.pem \
       -H=<registry-hostname>:2376 info
```

## 4. Verify Secure Access to Registry
```sh
docker login <registry-hostname> --tlsverify \
       --tlscacert=~/.docker/ca.pem --tlscert=~/.docker/cert.pem --tlskey=~/.docker/key.pem
```

## 5. Documentation Links
- [Docker TLS Authentication](https://docs.docker.com/engine/security/https/)
- [Using Secure Docker Registry](https://docs.docker.com/registry/deploying/)

## Conclusion
Certificate-based authentication ensures that only authorized Docker daemons can access images on a registry, enhancing security and compliance. Proper certificate management and secure storage are critical for maintaining integrity.

