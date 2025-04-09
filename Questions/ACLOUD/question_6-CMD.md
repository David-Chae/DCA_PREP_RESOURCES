## What does the CMD directive do?

The `CMD` directive in a Dockerfile specifies the **default command** that will be run when a container starts.

---

### 🧠 Key Points about `CMD`:

- It **doesn't** run during the image build — it only runs when a container **starts** from that image.
- You can **override** it at runtime using the `docker run` command.

---

### 🔧 Syntax Options:

1. **Exec form (preferred)**:
   ```Dockerfile
   CMD ["executable", "param1", "param2"]
   ```
   Example:
   ```Dockerfile
   CMD ["nginx", "-g", "daemon off;"]
   ```

2. **Shell form**:
   ```Dockerfile
   CMD command param1 param2
   ```
   Example:
   ```Dockerfile
   CMD echo "Hello from container"
   ```
   > Runs the command using `/bin/sh -c`.

---

### 📌 Important Behaviors:
- If the image is run **with a command**, that command **replaces** the `CMD`.
- If the image is run **without a command**, Docker uses the `CMD`.

---

### 💡 Example:

```Dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

If you run:
```bash
docker run my-node-app
```
It runs: `npm start`

If you run:
```bash
docker run my-node-app bash
```
It runs: `bash` instead — overriding the `CMD`.

---

## SAMPLE QUESTION : What does the CMD directive do?
```
1. It sets the default command for the image that runs if no other command is specified.
2. It executes a command during the build process.
3. It runs a command within the image and commits it to the result.
4. It runs a command on the host when the container starts.
```

The correct answer is:

> ✅ **It sets the default command for the image that runs if no other command is specified.**

---

### 🔍 Explanation of Each Option:

#### ✅ **"It sets the default command for the image that runs if no other command is specified."**
- **Correct.**
- This is exactly what `CMD` does — it defines the default command to execute **when the container starts**, unless overridden.

---

#### ❌ **"It executes a command during the build process."**
- **Incorrect.**
- That’s what `RUN` is for, not `CMD`.  
  `RUN` executes commands **while building the image**, `CMD` is for runtime.

---

#### ❌ **"It runs a command within the image and commits it to the result."**
- **Incorrect.**
- Again, this is describing what `RUN` does — it runs something and commits the result to the image layer.

---

#### ❌ **"It runs a command on the host when the container starts."**
- **Incorrect.**
- `CMD` runs **inside the container**, not on the host.

---

Let me know if you want to see how `CMD` interacts with `ENTRYPOINT`, or how to override it at runtime!
