## Which command enables us to build a secure overlay network? 
```sh
A. docker network create --opt encrypted --driver overlay my-net 
B. docker network create --opt encrypted my-net 
C. docker network create --encrypted --driver overlay my-net 
D. docker network create --secure --driver overlay my-net
```

The correct answer is:  

✔ **A. `docker network create --opt encrypted --driver overlay my-net`**  

### **Explanation:**  
- To create a **secure overlay network**, you must use the **overlay** driver and enable encryption.  
- The `--opt encrypted` flag ensures that **VXLAN traffic** between containers is **encrypted** using **IPSec**.
- The correct syntax follows this pattern:  
  ```sh
  docker network create --opt encrypted --driver overlay my-net
  ```

### **Why the other options are incorrect?**
1. **B. `docker network create --opt encrypted my-net`** ❌  
   - Incorrect because it **omits** the `--driver overlay` flag, which is required to create an overlay network.

2. **C. `docker network create --encrypted --driver overlay my-net`** ❌  
   - Incorrect because `--encrypted` is **not** a valid flag. The correct syntax is `--opt encrypted`.

3. **D. `docker network create --secure --driver overlay my-net`** ❌  
   - Incorrect because `--secure` is **not a valid flag** in Docker networking.

### **Final Answer:**  
✔ **A. `docker network create --opt encrypted --driver overlay my-net`**
