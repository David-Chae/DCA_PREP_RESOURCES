## 176. Will the given command return a list of volumes for a given container? docker container inspect nginx
A. Yes  
B. No  

✅ **Correct Answer: A. Yes**

---

### 📘 **Explanation:**

The command:

```bash
docker container inspect nginx
```

will return **detailed JSON output** about the container named `nginx`, including:

- Volume mounts  
- Networking information  
- Configuration  
- Environment variables  
- Image used  
- And much more.

---

### 🔍 **Volume Information:**

Inside the JSON output, under:

```json
"Mounts": [...]
```

you'll find a list of **volumes**, including:

- **Source** (host path or named volume)  
- **Destination** (mount point inside container)  
- **Type** (bind, volume, tmpfs)  
- **ReadOnly** flag

So yes — **`docker container inspect`** **does show the volumes used by the container**.

---

### ✅ **Final Answer: A. Yes**  
Let me know if you'd like to see a sample output or how to filter just the volumes from it.
