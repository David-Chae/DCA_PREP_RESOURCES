## When creating a container, how would we specify that the container should be attached to an existing network called my-network?
```
1. We can use docker run --attach my-network nginx.
2. We can use docker run --network my-network nginx.
3. We can use docker run --network-alias web nginx.
4. We can use docker run -n my-network nginx.
```


The correct answer is:

> ✅ **We can use `docker run --network my-network nginx`.**

---

### ✅ Explanation:

To attach a container to an **existing Docker network**, you use the `--network` flag with `docker run`.

**Syntax:**
```bash
docker run --network <network-name> <image>
```

So for your case:
```bash
docker run --network my-network nginx
```

This command runs an Nginx container and attaches it to the `my-network` network.

---

### ❌ Incorrect Options:

- **`docker run --attach my-network nginx`**  
  🔴 `--attach` is for connecting to **standard input/output/error** streams, **not for networks**.

- **`docker run --network-alias web nginx`**  
  ⚠️ Only valid **in conjunction with** `--network`. It's used to set an alias within a user-defined network.

  ✅ Example (but not correct alone):  
  ```bash
  docker run --network my-network --network-alias web nginx
  ```

- **`docker run -n my-network nginx`**  
  🔴 `-n` is **not a valid shorthand** for setting a network.

---

Let me know if you'd like to see how to **create a network** first, or how to **verify a container’s network config** after creation!
