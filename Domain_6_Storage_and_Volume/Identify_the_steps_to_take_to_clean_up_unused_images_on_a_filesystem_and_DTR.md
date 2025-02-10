
# Cleaning Up Unused Docker Images (Filesystem and DTR)

## Overview

Over time, unused Docker images can accumulate on your system, taking up valuable disk space. Cleaning up these images is crucial for maintaining a lean and efficient Docker environment. The process for cleaning up images on the local filesystem and in Docker Trusted Registry (DTR) is slightly different, and it is important to understand both processes for the Docker Certified Associate (DCA) exam.

This guide explains the steps to clean up unused images on both the filesystem and Docker Trusted Registry (DTR).

## Cleaning Up Unused Docker Images on the Filesystem

Docker images that are no longer in use can be cleaned up using Docker's built-in commands. Unused images typically result from outdated or intermediate images that are no longer needed.

### Step 1: Identify Unused Images
You can use the following command to list all images, including their size, repository, and tags:
```bash
docker images
```

To find unused images, look for images that are not associated with any container (i.e., they have no container ID listed under the `CONTAINER ID` column).

### Step 2: Remove Specific Unused Images
If you want to remove a specific image, use the `docker rmi` command followed by the image's name or ID:
```bash
docker rmi <image-name-or-id>
```

Example:
```bash
docker rmi my-old-image:latest
```

### Step 3: Clean Up Unused Images Automatically
You can automatically clean up unused images, containers, volumes, and networks that are not being used by any containers using the `docker system prune` command. This command will remove all dangling images, stopped containers, and unused volumes.

To remove unused images and other resources:
```bash
docker system prune
```

To prune all unused images (including untagged images), use the `-a` flag:
```bash
docker system prune -a
```

**Note**: The `docker system prune` command can be very aggressive, as it removes unused resources that are not associated with any containers. Ensure that you are not deleting resources that are important for your containers or applications.

### Step 4: Remove Dangling Images
Dangling images are images that are not tagged and are no longer associated with any containers. These images can be removed using:
```bash
docker image prune
```

To remove all dangling images, including those that are not tagged:
```bash
docker image prune -a
```

### Step 5: Clean Up Unused Docker Volumes
Volumes are also part of the Docker system, and unused volumes can consume disk space. You can remove unused volumes by running:
```bash
docker volume prune
```

### Step 6: Clean Up Unused Networks
Docker networks that are not in use can also be removed:
```bash
docker network prune
```

### Step 7: Verify Cleanup
After pruning, you can verify that the unused images and resources have been removed by listing the remaining images:
```bash
docker images
```

## Cleaning Up Unused Images in Docker Trusted Registry (DTR)

In Docker Trusted Registry (DTR), cleaning up unused images is crucial for managing disk space and keeping the registry organized. DTR provides a web interface and CLI tools to help manage repositories and images.

### Step 1: Identify Unused Images
DTR offers a web interface where you can see the images in your repositories. You can filter by tags, repositories, or creation dates to identify images that are no longer in use.

Alternatively, you can use the DTR API or CLI to list the repositories and images.

### Step 2: Remove Unused Images from DTR
Once you identify unused images in the DTR, you can remove them through the web interface or CLI.

#### Using the Web Interface:
- Navigate to the **Repositories** section in DTR.
- Select the repository you want to manage.
- Identify the tags or images that are no longer needed.
- Select the images and click **Delete**.

#### Using the DTR CLI:
You can use the `docker` CLI to interact with DTR. To delete an image, use the following command:
```bash
docker repository delete <repository-name>:<tag>
```

Example:
```bash
docker repository delete my-repository:old-tag
```

### Step 3: Automate Image Cleanup with Retention Policies
DTR allows you to set retention policies for your images, automatically deleting older images or those that are no longer in use. This is especially helpful for large-scale environments.

To set up retention policies:
- Go to the DTR web interface.
- Navigate to the **Retention Policies** section under the repository settings.
- Set rules for cleaning up old or unused images, such as deleting images older than a certain date or deleting images that have not been pulled in a specified time frame.

### Step 4: Verify Cleanup in DTR
After performing cleanup actions, check the repository to ensure that unused images have been removed and your storage space is free.

## Official Documentation for Further Reading

1. **Docker Image Management**:
   - [Managing Docker Images](https://docs.docker.com/engine/reference/commandline/image/)
   - [Docker System Prune](https://docs.docker.com/engine/reference/commandline/system_prune/)

2. **Docker Trusted Registry (DTR) Cleanup**:
   - [DTR Image Cleanup Documentation](https://docs.docker.com/ee/dtr/)
   - [DTR Retention Policies](https://docs.docker.com/ee/dtr/)

---

## Conclusion

Regularly cleaning up unused Docker images is essential for maintaining a clean and efficient Docker environment. By using commands like `docker system prune`, `docker image prune`, and managing retention policies in Docker Trusted Registry (DTR), you can easily free up disk space and ensure that your environment remains organized.
Good luck with your DCA exam preparation!
