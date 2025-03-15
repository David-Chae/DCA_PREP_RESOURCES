## Which of the following commands will limit the amount of active RAM a container uses to 1 GB? 
1. docker run --memory-swap 2G --memory-reservation 1G nginx 
2. docker run --memory-reservation 1G nginx 
3. docker run --memory-swap 2G nginx 
4. docker run --memory 1G nginx

The correct answer is:  

✅ **`docker run --memory 1G nginx`**  

### **Explanation:**  
- The **`--memory`** flag **directly limits** the amount of **active RAM** a container can use.  
- **`--memory 1G`** restricts the container to a maximum **1 GB of RAM**.  
- If the container tries to exceed this limit, it will be **throttled** or **killed** by the kernel's Out-of-Memory (OOM) manager.

### **Why the Other Options Are Incorrect:**
1. **`docker run --memory-swap 2G --memory-reservation 1G nginx`**  
   ❌ **Incorrect**:  
   - **`--memory-swap`** sets the **total memory + swap** limit, but **does not** directly limit active RAM.  
   - **`--memory-reservation`** only sets a **soft limit** (a preferred minimum, but not an enforced cap).  

2. **`docker run --memory-reservation 1G nginx`**  
   ❌ **Incorrect**:  
   - **`--memory-reservation`** is a **soft limit** that the container can exceed.  
   - It does **not** enforce a **hard** **1 GB RAM limit**.  

3. **`docker run --memory-swap 2G nginx`**  
   ❌ **Incorrect**:  
   - **`--memory-swap`** only sets the **total memory + swap** limit.  
   - It **does not** control the **RAM limit separately**.

### **Final Answer:**  
✅ **`docker run --memory 1G nginx`**
