## Which of the following commands can we use to view detailed metadata about a container? (Choose two)

```
docker metadata
docker container inspect
docker inspect
docker query
```

The correct answers are:

---

✅ **`docker container inspect`**  
✅ **`docker inspect`**

---

### 🧠 Explanation:

- **`docker container inspect`**  
  ✔️ This command provides **detailed metadata** (like environment variables, mounts, network settings, etc.) about a specific **container**.

- **`docker inspect`**  
  ✔️ This is a more general command that can be used for **containers**, **images**, **volumes**, **networks**, etc., by specifying the correct object.

---

### ❌ Incorrect Options:

- **`docker metadata`**  
  ❌ Not a valid Docker command.

- **`docker query`**  
  ❌ Also not a valid Docker command.

---

Would you like help reading or interpreting the output of `docker inspect`?
