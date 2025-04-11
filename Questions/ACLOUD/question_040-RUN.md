## vDescribe what the RUN directive does.
```
1. The RUN directive executes a command and commits the resulting changed files as a new layer in the image.
2. The RUN directive sets the default command for the image.
3. The RUN directive automatically runs a command when a new container gets created.
4. The RUN directive executes a command on the host when building an image.
```


Let's evaluate each option to determine what the `RUN` directive in a Dockerfile **actually does**:

---

### ✅ **Correct Answer:**
> **The RUN directive executes a command and commits the resulting changed files as a new layer in the image.**  
**✔️ True**

- This is the core purpose of `RUN`. It is used **during image build time**.
- The output (filesystem changes) of the command is **saved as a new layer** in the Docker image.

---

### ❌ **The RUN directive sets the default command for the image.**  
**False**

- This is the job of the `CMD` directive, not `RUN`.
- `CMD` defines what command runs when a container is started from the image.

---

### ❌ **The RUN directive automatically runs a command when a new container gets created.**  
**False**

- Again, this describes what `CMD` or `ENTRYPOINT` does.
- `RUN` is **not executed at runtime**, but **during image build**.

---

### ❌ **The RUN directive executes a command on the host when building an image.**  
**False**

- `RUN` commands are executed **within the image's build environment**, not on the host machine directly.
- The host only provides the Docker engine to facilitate the build.

---

### ✅ Summary Table:

| Statement                                                                 | True/False | Reason                                                                 |
|---------------------------------------------------------------------------|------------|------------------------------------------------------------------------|
| Executes a command and commits changed files as a new layer              | ✔️ True     | This is the correct behavior of the RUN directive during image build. |
| Sets the default command for the image                                   | ❌ False    | That’s what `CMD` is for.                                              |
| Runs a command when a new container gets created                         | ❌ False    | That’s `CMD` or `ENTRYPOINT`, not `RUN`.                              |
| Executes a command on the host when building the image                   | ❌ False    | RUN runs inside the image’s environment, not directly on the host.     |

Let me know if you’d like a visual breakdown of how a Dockerfile builds an image layer by layer!
