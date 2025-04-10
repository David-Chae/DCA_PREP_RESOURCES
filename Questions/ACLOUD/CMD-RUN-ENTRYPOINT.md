## What is the difference between CMD, RUN and ENTRYPOINT directives?

Great question! `CMD`, `RUN`, and `ENTRYPOINT` are all Dockerfile directives, but they serve **different purposes** and behave differently. Here's a breakdown:

---

### 🛠️ `RUN`
- **Purpose**: Executes a command **at build time** to modify the image.
- **Usage**: Used to install packages, set up the environment, etc.
- **Creates a new layer** in the image.
- **Example**:
  ```Dockerfile
  RUN apt-get update && apt-get install -y curl
  ```

---

### 🚀 `CMD`
- **Purpose**: Provides **default arguments** for the container's main process.
- **Used at runtime**, **overridden** by command-line arguments to `docker run`.
- Only **one `CMD`** is allowed — later ones override earlier ones.
- **Example**:
  ```Dockerfile
  CMD ["node", "app.js"]
  ```

---

### 🔗 `ENTRYPOINT`
- **Purpose**: Specifies the main command to **always run** in the container.
- Less likely to be overridden accidentally.
- Often used with `CMD` to provide default parameters.
- **Example**:
  ```Dockerfile
  ENTRYPOINT ["python3"]
  CMD ["script.py"]
  ```
  This will run: `python3 script.py`

---

### 🤔 Summary Table

| Directive     | When it runs    | Purpose                           | Overridable?      |
|---------------|------------------|------------------------------------|--------------------|
| `RUN`         | Build time       | Build image steps (install, copy)  | ❌ Not at runtime  |
| `CMD`         | Container start  | Default command/arguments          | ✅ Easily overridden |
| `ENTRYPOINT`  | Container start  | Main command (like `init`)         | ⚠ Only with `--entrypoint` or override in Dockerfile |

---

Let me know if you'd like a real-world example using all three!

