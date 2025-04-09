## How to ensure that a container uses a maximum of 1 GB of active memory?

To ensure that a container uses a maximum of **1 GB** of active memory, you can use the **`--memory`** option when running the container with the **`docker run`** command. This option allows you to set a hard limit on the amount of memory the container can use.

Here’s how you can do that:

### Command:
```bash
docker run --memory=1g <image_name>
```

### Explanation:
- **`--memory=1g`**: This sets the maximum amount of memory the container can use to **1 GB**.
  - You can also use other units like `m` for megabytes (e.g., `512m` for 512 MB).
  - Docker will enforce this limit by preventing the container from using more than the specified memory.

### Example:
If you want to run a **busybox** container and limit its memory usage to **1 GB**, the command would be:
```bash
docker run --memory=1g busybox
```

### Optional: Set Memory Swap Limits
You can also limit the **swap memory** in addition to the physical memory with the `--memory-swap` option:

```bash
docker run --memory=1g --memory-swap=1g <image_name>
```

- **`--memory-swap=1g`**: This ensures the total memory (RAM + swap) used by the container doesn't exceed 1 GB. If you set `--memory-swap` to the same value as `--memory`, it means no swap is allowed, and the container will be killed if it exceeds 1 GB.

### Important Notes:
- Docker enforces the memory limit at the container level, so the container will be restricted to the specified amount.
- If the container exceeds the memory limit, it will be **terminated** and the OOM (Out Of Memory) killer will kick in.

Let me know if you need further clarification!
