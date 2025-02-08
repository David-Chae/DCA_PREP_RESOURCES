
# Inspecting Docker Images Using Filter and Format Options

## Overview

Docker CLI provides powerful options to inspect images and report specific attributes using the `--filter` and `--format` flags. These options help you to quickly find and format the information you need from Docker images.

## Using Filter Option

The `--filter` flag allows you to filter output based on specific criteria. For example, you can filter images based on their labels or other attributes.

### Example: Filter Images by Label

To list images with a specific label, you can use the `--filter` flag:

```bash
docker images --filter "label=app=web"
```

In this example, the command filters images that have the label `app=web`.

## Using Format Option

The `--format` flag allows you to customize the output format using Go templates. This option helps you extract and format specific attributes of images.

### Example: Format Output to Show Image ID and Size

To format the output to display only the image ID and size, you can use the `--format` flag:

```bash
docker images --format "table {{.ID}}\t{{.Size}}"
```

In this example, the output is formatted as a table showing the image ID and size.

### Example: Detailed Image Inspection with Format

To inspect a specific image and format the output to show specific details, you can use the `docker inspect` command with the `--format` flag:

```bash
docker inspect --format='{{json .Config}}' <image_id_or_tag>
```

In this example, the command formats the output to display the configuration of the specified image in JSON format.

### Example: Custom Template for Inspect Output

To create a custom template to show specific attributes, you can use the `--format` flag with the `docker inspect` command:

```bash
docker inspect --format='{{.Id}}: {{.ContainerConfig.Cmd}}' <image_id_or_tag>
```

In this example, the output shows the image ID and the command that was used to create the container configuration.

## Suggested Documentation
- [docker image inspect](https://docs.docker.com/reference/cli/docker/image/inspect/)
- [Filter inspect results](https://docs.docker.com/reference/cli/docker/image/ls/#filtering)
- [Format inspect results](https://docs.docker.com/reference/cli/docker/image/ls/#format-the-output)

For more detailed information on using filter and format options with Docker CLI commands, refer to the following documentation:

