## 96. Bob has put up a new Docker server. The overlay2 driver is the server's default, but he prefers to use devicemapper. How could this modification be put into practice?
```sh
A. Set devicemapper as the storage-driver in /etc/docker/daemon.json.
B. In Docker's unit file, modify the dockerd call to include the --storage-driver flag
C. Change your Docker version.
D. Reformat the storage disk
```
The correct answer is: A & B

**A. Set devicemapper as the storage-driver in /etc/docker/daemon.json.**
**B. In Docker's unit file, modify the dockerd call to include the --storage-driver flag**

### Explanation:
Docker allows configuring its storage driver through the `daemon.json` file, which is the recommended way to make persistent changes. To switch from `overlay2` to `devicemapper`, Bob should:

1. Open the Docker daemon configuration file:
   ```bash
   sudo nano /etc/docker/daemon.json
   ```
2. Add or modify the following entry:
   ```json
   {
     "storage-driver": "devicemapper"
   }
   ```
3. Restart the Docker service:
   ```bash
   sudo systemctl restart docker
   ```

### Why the other options are incorrect:
- **B. In Docker's unit file, modify the dockerd call to include the --storage-driver flag**  
  While it is possible to specify the storage driver using the `--storage-driver` flag when starting the Docker daemon, modifying systemd unit files manually is not the recommended approach because changes may be overwritten by updates.

- **C. Change your Docker version**  
  There is no need to change the Docker version unless the installed version does not support `devicemapper`. Devicemapper became a deprecated storage driver and was removed from Docker Engine from v25.0. To use devicemapper, docker version has to be below v25.0. (https://docs.docker.com/engine/storage/drivers/device-mapper-driver/)

- **D. Reformat the storage disk**  
  Reformatting the disk is unnecessary to change the storage driver. However, if the `devicemapper` driver is using direct-lvm mode, additional disk setup might be required.

Thus, **A** is the best choice. 🚀
The Device Mapper driver has been deprecated, and is removed in Docker Engine v25.0. If you are using Device Mapper, you must migrate to a supported storage driver before upgrading to Docker Engine v25.0. Read the Docker storage drivers page for supported storage drivers.
