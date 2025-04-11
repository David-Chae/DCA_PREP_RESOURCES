## What command would we use to locate the layered file system data for an image on a machine?
```
1. docker image layers
2. docker image inspect
3. docker layer inspect
4. docker pull history
```

✅ **Correct answer:**  
**`docker image inspect`**

---

### ✅ Explanation:

The `docker image inspect` command provides **detailed information** about a Docker image, including:

- Its **layered filesystem structure**
- **Layer digests (IDs)**
- Metadata like environment variables, commands, entrypoint, working directory, etc.

To view the layered file system data, you'd run:

```bash
docker image inspect <image-name>
```

Look for the `"RootFS"` or `"Layers"` section in the output.

---

### ❌ Why the other options are incorrect:

- **`docker image layers`** – ❌ Not a valid Docker command.
- **`docker layer inspect`** – ❌ Also not a valid Docker command.
- **`docker pull history`** – ❌ No such command; probably a confusion with `docker history`, which **shows a high-level history of an image**, but not detailed layer filesystem data.

---

Let me know if you want help interpreting the `inspect` output or tracking layer sizes!
