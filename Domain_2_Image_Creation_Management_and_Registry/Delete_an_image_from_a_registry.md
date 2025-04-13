
# Deleting a Docker Image from a Registry

## Overview

Deleting a Docker image from a registry involves using the registry's API or user interface. The process may vary depending on the type of registry you are using (e.g., Docker Hub, Azure Container Registry, Amazon ECR, etc.). This guide provides general instructions for deleting images from a Docker registry.

## Steps to Delete a Docker Image from Registry

If you're using the **local Docker registry** (the one running with `docker run -p 5000:5000 registry:2`), here's how you can:

---

## ✅ 1. 📋 **Check Images in Your Local Registry**

The Docker Registry API v2 doesn't have a pretty UI by default, but you can query it using `curl` or a browser.

### 🔍 List Repositories

```bash
curl http://localhost:5000/v2/_catalog
```

Example response:
```json
{
  "repositories": ["myapp", "nginx", "alpine"]
}
```

### 🔍 List Tags for a Repository

```bash
curl http://localhost:5000/v2/myapp/tags/list
```

Example response:
```json
{
  "name": "myapp",
  "tags": ["latest", "v1"]
}
```

---

## 🧹 2. ❌ **Remove Image from Local Registry**

Unfortunately, the default Docker registry **does not support deletion via API** out of the box. But you can do it by:

### Option A: Use Registry with Delete Support Enabled

You must run the registry with **delete enabled**:

```bash
docker run -d \
  -p 5000:5000 \
  -e REGISTRY_STORAGE_DELETE_ENABLED=true \
  --name registry \
  registry:2
```

### Then perform these steps:

#### 📌 Step 1: Get image digest

```bash
curl -v http://localhost:5000/v2/myapp/manifests/latest \
  -H "Accept: application/vnd.docker.distribution.manifest.v2+json"
```

Look for a response header like this:
```
Docker-Content-Digest: sha256:<digest>
```

#### 📌 Step 2: Delete the image by digest

```bash
curl -X DELETE http://localhost:5000/v2/myapp/manifests/sha256:<digest>
```

---

## 🚮 3. (Optional) Garbage Collect

Even after deletion, the blob still exists until garbage collection is run.

```bash
docker exec registry bin/registry garbage-collect /etc/docker/registry/config.yml
```

Make sure no active pushes/pulls are happening when you do this.

---

## 🧪 Pro Tip: Use UI for Easier Browsing

You can use a UI like **[Portus](https://github.com/SUSE/Portus)** or **[docker-registry-ui](https://github.com/Joxit/docker-registry-ui)** to view and manage images visually.

---



### Step 1: Log into the Registry

Before deleting an image, ensure you are logged into the registry. Use the `docker login` command followed by the registry's address:

```bash
docker login <registry_address>
```

For example, to log into Docker Hub:

```bash
docker login
```

### Step 2: List the Images in the Registry

List the images in your registry to find the image you want to delete. Use the registry's user interface or API to view the available images.

### Step 3: Delete the Image

#### Using Docker Hub

To delete an image from Docker Hub, follow these steps:

1. Log in to Docker Hub through a web browser.
2. Navigate to the repository containing the image.
3. Select the image tag you want to delete.
4. Click the "Delete" button and confirm the deletion.






#### Using Azure Container Registry

To delete an image from Azure Container Registry, use the Azure CLI:

```bash
az acr repository delete --name <registry_name> --image <repository_name>:<tag> --yes
```

For example:

```bash
az acr repository delete --name myRegistry --image myRepository:latest --yes
```

#### Using Amazon ECR

To delete an image from Amazon ECR, use the AWS CLI:

```bash
aws ecr batch-delete-image --repository-name <repository_name> --image-ids imageTag=<tag>
```

For example:

```bash
aws ecr batch-delete-image --repository-name myRepository --image-ids imageTag=latest
```

Here is a markdown file that explains how to delete a Docker image from a private registry, along with suggested documentation:


# Deleting a Docker Image from a Private Registry



## Overview

Deleting a Docker image from a private registry involves using the registry's API or user interface. The process may vary depending on the type of registry you are using. This guide provides general instructions for deleting images from a private Docker registry.

## Steps to Delete a Docker Image from a Private Registry

### Step 1: Log into the Registry

Before deleting an image, ensure you are logged into the registry. Use the `docker login` command followed by the registry's address:

```bash
docker login <registry_address>
```

For example, to log into a private registry:

```bash
docker login myregistry.example.com
```

### Step 2: List the Images in the Registry

List the images in your registry to find the image you want to delete. Use the registry's user interface or API to view the available images.

### Step 3: Delete the Image

#### Using Registry API

Many private registries provide an API to manage images. To delete an image using the API, you may need to use a tool like `curl` to send a DELETE request. Refer to your registry's documentation for specific API endpoints.

Example for deleting an image using a hypothetical registry API:

```bash
curl -X DELETE https://myregistry.example.com/v2/myrepository/myimage/manifests/<digest>
```

In this example, replace `<digest>` with the specific digest of the image you want to delete.

#### Using User Interface

If your private registry has a user interface, follow these general steps:

1. Log in to the registry's web interface.
2. Navigate to the repository containing the image.
3. Select the image tag you want to delete.
4. Click the "Delete" button and confirm the deletion.

### Example for Docker Registry (Open Source)

If you are using the open-source Docker Registry, you can delete an image by following these steps:

1. Find the image digest by running:

```bash
curl -X GET https://myregistry.example.com/v2/myrepository/myimage/manifests/latest | jq -r '.config.digest'
```

2. Use the digest to delete the image:

```bash
curl -X DELETE https://myregistry.example.com/v2/myrepository/myimage/manifests/<digest>
```

Replace `<digest>` with the digest obtained from the previous command.

Here is a markdown file that explains how to delete a Docker image from Docker Trusted Registry (DTR), along with suggested documentation:


# Deleting a Docker Image from Docker Trusted Registry (DTR)


## Overview

Deleting a Docker image from Docker Trusted Registry (DTR) involves using the DTR user interface or API. This guide provides instructions on how to delete images from DTR.

## Steps to Delete a Docker Image from DTR

### Step 1: Log into DTR

Before deleting an image, ensure you are logged into DTR. Use the DTR web interface to log in with your credentials.

### Step 2: Navigate to the Repository

Once logged in, navigate to the repository containing the image you want to delete.

### Step 3: Delete the Image

1. **Using the DTR User Interface**:
   - Find the image tag you want to delete.
   - Click on the image tag to open its details.
   - Click the "Delete" button and confirm the deletion.

2. **Using the DTR API**:
   - Send a DELETE request to the DTR API endpoint for the specific image.
   - Replace `<digest>` with the specific digest of the image you want to delete.

Example API request:

```bash
curl -X DELETE https://dtr.example.com/v2/repositories/<namespace>/<repository>/manifests/<digest>
```

Replace `<namespace>`, `<repository>`, and `<digest>` with the appropriate values for your image.

## Suggested Documentation

For more detailed information on deleting Docker images from DTR, refer to the following documentation:

- [Docker Trusted Registry API Reference](https://docs.docker.com/registry/spec/api/)
- [Docker Hub Documentation - Managing Images](https://docs.docker.com/docker-hub/repos/#managing-images)
- [Azure Container Registry Documentation - Repositories](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-repository-scoped-permissions)
- [Amazon ECR Documentation - Deleting Images](https://docs.aws.amazon.com/AmazonECR/latest/userguide/delete_image.html)
