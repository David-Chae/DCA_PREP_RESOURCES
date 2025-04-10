How would we create a volume called new-volume without running a container?
```
1. We would run docker volume create new-volume.
2. We would run docker create volume new-volume.
3. We would run docker run --rm -v new-volume:/tmp nginx.
4. We would use docker run -v new-volume:/tmp nginx.
```

The correct answer is:

**We would run `docker volume create new-volume`.**

### Explanation:

- **`docker volume create new-volume`**: This command is used to create a new Docker volume without needing to run a container. It directly creates the volume on the Docker host, allowing it to be used by containers later.

### Why the other options are incorrect:

- **`docker create volume new-volume`**: This is **not a valid Docker command**. There is no `create volume` subcommand in Docker.

- **`docker run --rm -v new-volume:/tmp nginx`**: This command runs a container and attaches the volume `new-volume` to the `/tmp` directory inside the container. However, the volume is created implicitly when the container is run. This is not the same as explicitly creating the volume without running a container.

- **`docker run -v new-volume:/tmp nginx`**: Similar to the previous option, this command runs a container with the `new-volume` volume attached, but it will only create the volume if it doesn't already exist. It still requires running a container, which isn't what you're asking for.

### Summary:
To **create a volume** without running a container, you should use **`docker volume create new-volume`**.
