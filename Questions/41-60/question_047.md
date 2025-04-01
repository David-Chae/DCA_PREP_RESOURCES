## 47. Which network driver connects containers directly to a network stack on the host machine without isolation?
```sh
A. host
B. none
C. macvlan
D. bridge
```

The correct answer is:  

**A. host**  

### Explanation:  
The `host` network driver allows containers to connect directly to the network stack of the host machine without any isolation. This means the container shares the host's network interfaces and can access the same IP address as the host, resulting in no network isolation.

### Why not the others?  
- **B. none**: The `none` driver provides no network access to the container.  
- **C. macvlan**: The `macvlan` driver gives containers their own MAC addresses and connects them directly to the physical network, but it still provides some isolation from the host’s network.  
- **D. bridge**: The `bridge` driver creates an isolated network for containers and uses a virtual bridge on the host to connect them.
