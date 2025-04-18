## Which of the instructions below will start a new bridge network? 
1. docker network create --network-driver bridge my-network 
2. docker network create --network bridge my-network 
3. docker network create --driver overlay my-network 
4. docker network create my-network

The correct answer is:  

✅ **`docker network create --driver bridge my-network`**  
or -d flag can be used instead of --driver
---

### Explanation:  
To create a new **bridge** network in Docker, you must specify the **bridge driver** explicitly. The correct syntax is:  

```sh
docker network create --driver bridge my-network
```
OR  
```sh
docker network create --d bridge my-network
```
Both **`--driver`** and **`--d`** are valid options.

---

### Why the Other Options Are Incorrect:  

❌ **`docker network create --network bridge my-network`**  
- There is **no `--network` flag** when creating a network. The correct flag is `--driver` or `--network-driver`.

❌ **`docker network create --driver overlay my-network`**  
- This creates an **overlay network**, not a **bridge network**. Overlay networks are used in **Docker Swarm** for multi-host communication.

❌ **`docker network create my-network`**  
- This creates a network, but **by default, it uses the `bridge` driver**. However, explicitly specifying `--driver bridge` ensures you get the intended behavior.

---

### Summary:  
To create a **bridge network**, use:  
```sh
docker network create --driver bridge my-network
```
