
# Managing Docker Images with CLI Commands

## Listing Images

To list all Docker images on your system, use the `docker images` command.

```bash
docker images
```

This will display a list of all images, including their repository, tag, image ID, creation date, and size.

## Deleting Images

To delete one or more Docker images, use the `docker rmi` command followed by the image ID or tag.

```bash
docker rmi <image_id_or_tag>
```

For example, to delete an image with the ID `abc123`, you would run:

```bash
docker rmi abc123
```

## Pruning Images

To remove unused Docker images, use the `docker image prune` command. This will delete all images that are not currently in use by a running container.

```bash
docker image prune
```

You can use the `-a` flag to remove all unused images, including those associated with stopped containers.

```bash
docker image prune -a
```

## Inspecting Images

To view detailed information about a specific Docker image, use the `docker inspect` command followed by the image ID or tag.

```bash
docker inspect <image_id_or_tag>
```

## Tagging Images

To tag a Docker image, use the `docker tag` command. This assigns a new tag to an existing image.

```bash
docker tag <image_id> <new_tag>
```

For example, to tag an image with ID `abc123` as `myimage:latest`, you would run:

```bash
docker tag abc123 myimage:latest
```

## Saving Images

To save a Docker image to a tar file, use the `docker save` command followed by the image ID or tag and the output file name.

```bash
docker save -o <output_file.tar> <image_id_or_tag>
```

For example, to save an image with ID `abc123` to a file named `myimage.tar`, you would run:

```bash
docker save -o myimage.tar abc123
```

## Loading Images

To load a Docker image from a tar file, use the `docker load` command followed by the input file name.

```bash
docker load -i <input_file.tar>
```

For example, to load an image from a file named `myimage.tar`, you would run:

```bash
docker load -i myimage.tar
```

## Suggested Documentation

For more detailed information on managing Docker images with CLI commands, refer to the following documentation:
- [docker image ls](https://docs.docker.com/reference/cli/docker/image/ls/)
- [docker image rm](https://docs.docker.com/reference/cli/docker/image/rm/)
- [docker image prune](https://docs.docker.com/reference/cli/docker/image/prune/)

- [Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/cli/)
- [Managing Docker Images](https://docs.docker.com/engine/reference/commandline/image/)
- [Best Practices for Docker CLI](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

These resources provide comprehensive insights into Docker CLI commands, best practices, and examples to help you manage Docker images efficiently.
