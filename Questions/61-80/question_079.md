## When building a volume alongside a service that uses docker service create, what flag should we use to define a custom volume driver?
A. --volumedriver <driver>  
B.--driver <driver>  
C. --volume-driver <driver>  
D. --mount volume-driver=<driver>  

The correct answer is:  

✔ **C. `--volume-driver <driver>`**  

---

### **Explanation:**  
When creating a service with `docker service create`, you can specify a **custom volume driver** using the `--volume-driver` flag. This tells Docker which storage driver to use when managing volumes for the service.  

Example:  
```sh
docker service create --name my-service \
  --volume-driver my-custom-driver \
  --mount source=my-volume,target=/app \
  nginx
```

---

### **Why are the other options incorrect?**  

1. **A. `--volumedriver <driver>`** ❌  
   - This is **not a valid Docker flag**.  

2. **B. `--driver <driver>`** ❌  
   - The `--driver` flag is used when creating a **volume** (e.g., `docker volume create --driver`), but **not** when using `docker service create`.  

3. **D. `--mount volume-driver=<driver>`** ❌  
   - The correct syntax for the `--mount` option does **not** include `volume-driver=...`. Instead, you define the driver separately with `--volume-driver`.  

---

### **Final Answer:**  
✔ **C. `--volume-driver <driver>`**
