## 77. Which of the following approaches can we use to effectively set the default DNS server for each container on a host?
```sh
A. use --dns flag with docker run
B. Edit the /etc/hosts file on the host
C. set "dns" in /etc/docker/deamon.json
D. use docker config set dns
```

The correct answer is:  

**C. set "dns" in /etc/docker/daemon.json**  

### Explanation:  
To set the default DNS server for all containers on a Docker host, you can specify the `dns` option in the **`/etc/docker/daemon.json`** file. This ensures that all containers running on that host will use the specified DNS server by default.

Example:
```json
{
  "dns": ["8.8.8.8", "8.8.4.4"]
}
```
After making this change, you need to restart the Docker daemon for it to take effect.

### Why not the others?  
- **A. use --dns flag with docker run**: This flag sets the DNS server for a specific container when it is started, but it does not set the default for all containers.  
- **B. Edit the /etc/hosts file on the host**: Editing the `/etc/hosts` file on the host does not change the DNS server settings for containers; it only affects hostname resolution for the host system itself.  
- **D. use docker config set dns**: There is no `docker config set dns` command for managing DNS settings in Docker. The correct way to configure DNS servers for all containers is through the `daemon.json` file.
