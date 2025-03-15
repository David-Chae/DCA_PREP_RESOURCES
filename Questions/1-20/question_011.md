## When building it, how would we specify that a container is joined to a network called my-network? 
1. We can use docker run -n my-network nginx. 
2. We can use docker run --network-alias web nginx. 
3. We can use docker run --attach my-network nginx. 
4. docker run --network my-network nginx can be used. 

The correct answer is:  

✅ **`docker run --network my-network nginx`**  

---

### Explanation:  
When running a container, you can specify which **Docker network** it should be attached to using the **`--network`** flag.  

**Syntax:**  
```sh
docker run --network <network-name> <image>
```
For example, to run an **nginx** container in the **"my-network"** network:  
```sh
docker run --network my-network nginx
```

---

### Why the Other Options Are Incorrect:  

❌ **`docker run -n my-network nginx`**  
- Docker **does not have a `-n` flag** for specifying a network. This option does not exist.  

❌ **`docker run --network-alias web nginx`**  
- `--network-alias` **only works inside Docker Compose or user-defined networks** but does not assign the container to a network. The container must already be attached to a user-defined **bridge** or **overlay** network.  

❌ **`docker run --attach my-network nginx`**  
- `--attach` is used to **attach to container input/output streams**, not for networks.  

---

### Summary:  
To connect a container to a specific network when starting it, use:  
```sh
docker run --network my-network nginx
```
