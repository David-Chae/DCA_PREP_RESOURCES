# Creating UCP Client Bundles

## Introduction
Docker **Universal Control Plane (UCP)** client bundles allow users to securely interact with a UCP-managed cluster from the command line by authenticating and authorizing API requests.

## 1. Why Use UCP Client Bundles?
- Provides **secure authentication** to the UCP API.
- Enables **CLI-based** management of Docker Enterprise clusters.
- Facilitates **automated and remote** interactions with UCP.

## 2. Generating a UCP Client Bundle

### a. Using the UCP Web UI
1. Log in to **UCP Web UI**.
2. Navigate to **User Settings** (top-right corner).
3. Select **Client Bundles**.
4. Click **Create Client Bundle**.
5. Download and extract the bundle (`.zip` file).

### b. Using the UCP CLI
1. Authenticate to UCP:
   ```sh
   docker login <ucp-url>
   ```
2. Request and download the bundle:
   ```sh
   docker run --rm \
     --name ucp-bundle \
     -v "$PWD:/mnt" \
     docker/ucp:latest \
     client-bundle -u <username> -p <password> --url <ucp-url>
   ```
3. Extract the downloaded `.zip` file:
   ```sh
   unzip ucp-bundle-<username>.zip -d ucp-bundle
   ```

## 3. Using the Client Bundle
After downloading, configure the environment:
```sh
export DOCKER_TLS_VERIFY=1
export DOCKER_CERT_PATH="$PWD/ucp-bundle"
export DOCKER_HOST=tcp://<ucp-url>:443
```
Now, use Docker commands securely:
```sh
docker info
docker node ls
```

## 4. Official Documentation
- [Configure the client bundle](https://docs.mirantis.com/mke/3.8/ops/access-cluster/client-bundle/configure-client-bundle.html)
- [Download the client bundle](https://docs.mirantis.com/mke/3.8/ops/access-cluster/client-bundle/download-client-bundle.html)

## Conclusion
UCP Client Bundles enable **secure and authenticated** access to UCP-managed clusters from the command line. By following these steps, you can efficiently manage your UCP environment remotely and securely.
