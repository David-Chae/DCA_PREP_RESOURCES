
# Displaying Layers of a Docker Image

## Overview

Docker images are built in layers, with each instruction in a Dockerfile creating a new layer. You can inspect these layers to understand how an image was constructed. Docker provides commands to display detailed information about the layers of an image.

## Using `docker history` to Display Layers

The `docker history` command shows the history of an image, including the creation time, size, and command used to create each layer.

### Example

To display the layers of an image, use the following command:

```bash
docker history <image_id_or_tag>
```

For example, to display the layers of an image with the tag `nginx:latest`, you would run:

```bash
docker history nginx:latest
```

### Example Output

```
IMAGE           CREATED         CREATED BY                                      SIZE                COMMENT
abc123          2 days ago      /bin/sh -c #(nop)  CMD ["nginx" "-g" "daemon …   0B
def456          2 days ago      /bin/sh -c #(nop)  EXPOSE 80                    0B
ghi789          2 days ago      /bin/sh -c apt-get update && apt-get install …   64MB
...
```

Each row represents a layer, showing the image ID, creation time, command, size, and any comments.

## Using `docker inspect` to Display Detailed Information

The `docker inspect` command provides detailed information about an image, including its layers. You can use this command with the `--format` flag to display specific attributes.

### Example

To display the layers of an image in JSON format, use the following command:

```bash
docker inspect --format='{{json .RootFS.Layers}}' <image_id_or_tag>
```

For example, to display the layers of an image with the tag `nginx:latest`, you would run:

```bash
docker inspect --format='{{json .RootFS.Layers}}' nginx:latest
```

### Example Output

```json
[
    "sha256:abc123...",
    "sha256:def456...",
    "sha256:ghi789..."
]
```

The output is a JSON array containing the layer IDs.

## Suggested Documentation

For more detailed information on inspecting Docker images and displaying layers, refer to the following documentation:

- [Docker CLI Reference - history](https://docs.docker.com/engine/reference/commandline/history/)
- [Docker CLI Reference - inspect](https://docs.docker.com/engine/reference/commandline/inspect/)
- [Understanding Docker Image Layers](https://docs.docker.com/develop/develop-images/baseimages/)
