## 205. Which command do you use to create a new swarm?  
A. docker swarm init --advertise-addr <MANAGER-IP>  
B. docker swarm init  
C. docker swarm init --advertise-addr <MANAGER-IP> --listen-addr <LISTEN-ADDR>  
D. docker swarm init --autolock  

The correct answers are:  

✅ **A. `docker swarm init --advertise-addr`**  
✅ **B. `docker swarm init`**  

### Explanation:  
- **`docker swarm init`** (Option B) initializes a new Swarm. By default, it automatically selects an IP address for the manager node.  
- **`docker swarm init --advertise-addr <ip>`** (Option A) explicitly specifies the IP address for the Swarm manager node, making it more suitable for multi-network environments.  

### Incorrect Options:  
- **C. `docker swarm init --advertise-addr --listen-addr`** ❌  
  - This command is **incorrect** because `--advertise-addr` requires an IP argument. It should be something like:  
    ```sh
    docker swarm init --advertise-addr <ip> --listen-addr <ip:port>
    ```  
- **D. `docker swarm init --autolock`** ❌  
  - The `--autolock` flag enables automatic encryption key locking but **does not initialize a Swarm by itself**. It must be used alongside a valid `docker swarm init` command.  

Would you like me to refine this into a structured DOMC format with eliminations? 🚀
