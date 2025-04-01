## What Linux feature does Docker use to allow containers to listen on ports lower than 1024 without running as root on the host? 
```sh
1. Linux jails
2. Capabilities
3. Namespaces
4. Control Groups
```

The correct answer is:  

✅ **Capabilities**  

### **Explanation:**  
- In Linux, **ports lower than 1024** (known as **privileged ports**) usually require **root privileges** to bind.  
- Docker **avoids running containers as root** while still allowing them to bind to privileged ports using **Linux capabilities**.  
- Specifically, **Docker grants the `CAP_NET_BIND_SERVICE` capability** to containers by default, allowing them to bind to ports **below 1024** without requiring full root privileges.  

### **Why the Other Options Are Incorrect:**  
❌ **Linux jails**  
- **Linux jails do not exist**—this is a FreeBSD feature, not Linux.  

❌ **Namespaces**  
- **Namespaces** isolate resources (e.g., network, processes, users) but **do not grant fine-grained permissions like binding to privileged ports**.  
- **Namespaces alone wouldn't let a container bind to ports < 1024 without root.**  

### **Final Answer:**  
✅ **Capabilities** (specifically `CAP_NET_BIND_SERVICE`)
