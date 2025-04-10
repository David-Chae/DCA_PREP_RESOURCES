## Which of the following commands would we use to retrieve a list of volumes on the current machine?
```
1. docker volume inspect
2. docker volume ps
3. docker volume ls
4. docker volume rm
```

The correct answer is **`docker volume ls`**.

### Explanation:

- **`docker volume ls`**: This command lists all the volumes on the current Docker host. It displays the names and additional details about the volumes, such as their driver.

### Why the other commands are incorrect:

- **`docker volume inspect`**: This command is used to retrieve detailed information about a specific volume (such as the mount point, driver, and configuration), but it requires the volume name as an argument. It doesn't list all volumes.

- **`docker volume ps`**: This command is **not valid** in Docker. There is no `ps` subcommand for volumes.

- **`docker volume rm`**: This command is used to remove one or more volumes. It doesn't list the volumes.

### Summary:
To retrieve a list of volumes on the current machine, you should use **`docker volume ls`**.
