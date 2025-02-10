# Enabling Docker Content Trust (DCT)

## Introduction
Docker Content Trust (DCT) ensures that images are **signed** and **verified** before being pulled or run, providing an added layer of security. It prevents the use of **tampered or untrusted images**.

## 1. Why Enable Docker Content Trust?
- Ensures **image integrity** and authenticity.
- Prevents **unauthorized modifications**.
- Enforces a policy to use only **signed images**.
- Enhances **supply chain security** in Docker workflows.

## 2. Enabling Docker Content Trust
Docker Content Trust is disabled by default. To enable it:

### a. Enable DCT for a Single Command
Set `DOCKER_CONTENT_TRUST=1` before running `docker pull`, `docker push`, or `docker run`.
```sh
DOCKER_CONTENT_TRUST=1 docker pull myregistry.com/myimage:latest
```

### b. Enable DCT System-Wide
To enable DCT for all Docker commands, set the environment variable globally:

#### On Linux/macOS:
```sh
echo 'export DOCKER_CONTENT_TRUST=1' >> ~/.bashrc
source ~/.bashrc
```

#### On Windows (PowerShell):
```powershell
$env:DOCKER_CONTENT_TRUST=1
```

## 3. Signing an Image with Notary
To sign an image, follow these steps:

### a. Generate Signing Keys
```sh
docker trust key generate mykey
```

### b. Enable Trust for a Repository
```sh
docker trust signer add --key mykey.pub myuser myregistry.com/myimage
```

### c. Push a Signed Image
```sh
DOCKER_CONTENT_TRUST=1 docker push myregistry.com/myimage:latest
```

### d. Verify the Image Signature
```sh
docker trust inspect --pretty myregistry.com/myimage:latest
```

## 4. Verifying DCT Enforcement
Once DCT is enabled, trying to pull an **unsigned image** will fail:
```sh
DOCKER_CONTENT_TRUST=1 docker pull unsignedimage:latest
```
**Output:**
```
Error: remote trust data does not exist for unsignedimage:latest
```

## 5. Official Documentation
- [Docker Content Trust](https://docs.docker.com/engine/security/trust/)
- [Docker Notary](https://docs.docker.com/notary/getting_started/)

## Conclusion
Docker Content Trust ensures only signed and verified images are used in your deployments. By enabling DCT and using **Notary**, you can enhance container security and integrity in production environments.
