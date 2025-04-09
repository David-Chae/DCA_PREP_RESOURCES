## We have set a value for "log-level" in /etc/docker/daemon.json. How would we set up the same value by passing a flag to dockerd instead?

To set the **log-level** value by passing a flag to **`dockerd`** instead of setting it in the `/etc/docker/daemon.json` file, you can use the `--log-level` flag when starting the Docker daemon.

Here's how you can set the `log-level` flag:

### Command:
```bash
dockerd --log-level=<level>
```

### Explanation:
- **`dockerd`**: This is the command to start the Docker daemon.
- **`--log-level=<level>`**: This flag allows you to set the logging level for Docker. The `<level>` should be replaced with one of the following values:
  - `debug`
  - `info` (default)
  - `warn`
  - `error`
  - `fatal`

For example, if you want to set the log level to **`debug`**, you would run:

```bash
dockerd --log-level=debug
```

### How it works:
- This flag will override the `log-level` setting in **`/etc/docker/daemon.json`** if it's set.
- It's useful for one-time changes or for debugging without needing to modify the configuration file directly.

If you're running Docker as a service, you can edit the service configuration to include this flag or pass it to the service when starting it.

---


No, the command `systemctl restart dockerd --log-level=debug` will not work as expected, because `systemctl` doesn't accept additional flags directly in the way you're trying to pass them. Instead, you'll need to modify the **Docker service** to include the `--log-level=debug` flag.

Here’s how to set the `log-level` flag for Docker when using `systemctl`:

### Steps:

1. **Edit the Docker service file**:
   - On most systems, the Docker service file is located at `/lib/systemd/system/docker.service` or `/etc/systemd/system/docker.service` (this may depend on your distribution).

   Run this command to open the service file for editing:
   ```bash
   sudo nano /etc/systemd/system/docker.service
   ```

2. **Modify the ExecStart line**:
   - Find the line starting with `ExecStart=`. This is the command that is run when Docker is started.
   - Add the `--log-level=debug` flag to it.

   It should look something like this:

   ```bash
   ExecStart=/usr/bin/dockerd --log-level=debug
   ```

3. **Reload the systemd configuration**:
   After modifying the service file, reload the systemd configuration to apply the changes:
   ```bash
   sudo systemctl daemon-reload
   ```

4. **Restart the Docker service**:
   Now, restart the Docker service with the following command:
   ```bash
   sudo systemctl restart docker
   ```

### Alternative: Use `EnvironmentFile`
You can also pass flags to Docker using an environment file, such as `/etc/docker/daemon.json`, or you can set them in a separate environment file and reference it in the systemd unit configuration.

---

Once you've done this, Docker will start with the `log-level=debug` flag, and you'll see more verbose logging.
