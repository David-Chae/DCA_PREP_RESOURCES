## What commands will run a busybox container and automatically delete it once it exits?

To run a **BusyBox** container and automatically delete it once it exits, you can use the following command:

```bash
docker run --rm busybox
```

### Explanation:
- **`docker run`**: Runs a new container.
- **`--rm`**: Automatically removes the container once it exits (i.e., once the container stops running).
- **`busybox`**: Specifies the image to use, in this case, the **BusyBox** image.

This command will run a **BusyBox** container, and once the container finishes its task or exits, Docker will automatically remove it.

If you want the container to run a specific command (like `echo`), you can specify it after the image name:

```bash
docker run --rm busybox echo "Hello, World!"
```

This will run the BusyBox container, execute the `echo "Hello, World!"` command, and then automatically remove the container once it exits.

---

## SAMPLE QUESTION : Which of the following commands will run a busybox container and automatically delete it once it exits?
```
docker run --restart no busybox
docker run --rm busybox
docker run --rm --restart on-failure busybox
docker container rm busybox
```
The correct command is:

> ✅ **`docker run --rm busybox`**

---

### Explanation of Each Option:

#### ✅ **`docker run --rm busybox`**
- **Correct.**
- This command will **run** the **busybox** container and **automatically delete** it once it exits, due to the `--rm` flag.
- The `--rm` flag ensures that the container is removed as soon as it stops, helping to avoid clutter from exited containers.

---

#### ❌ **`docker run --restart no busybox`**
- **Incorrect.**
- The `--restart no` option disables automatic restarts of the container. However, it **does not automatically remove** the container once it exits.
  
---

#### ❌ **`docker run --rm --restart on-failure busybox`**
- **Incorrect.**
- The `--rm` flag will still remove the container after it exits, but the `--restart on-failure` flag tells Docker to restart the container if it exits with a non-zero exit code. This is not relevant to the question, as it doesn’t guarantee the container is automatically deleted after it exits.

---

#### ❌ **`docker container rm busybox`**
- **Incorrect.**
- This command removes an **existing container** (named `busybox`), but it will not run a new container. It does not automatically delete a container after it exits.

---

So, the correct choice is `docker run --rm busybox`, which will start the BusyBox container and automatically remove it when it exits.
