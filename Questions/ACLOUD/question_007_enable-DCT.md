## How can you enable Docker Content Trust (DCT) in Docker Community Edition (CE)?

To enable **Docker Content Trust (DCT)** in Docker Community Edition (CE), you need to set the **`DOCKER_CONTENT_TRUST`** environment variable to **`1`**. This ensures that Docker verifies the authenticity and integrity of images by requiring the use of **signatures** when pulling or pushing images.

---

### 🛠️ How to Enable Docker Content Trust:

1. **Set the environment variable**:
   - **On Linux/macOS**:
     ```bash
     export DOCKER_CONTENT_TRUST=1
     ```
   - **On Windows (PowerShell)**:
     ```powershell
     $env:DOCKER_CONTENT_TRUST="1"
     ```

   You can add this line to your shell’s profile (e.g., `.bashrc` or `.zshrc` for Linux/macOS) to make it persistent across sessions.

2. **Verify the setting**:
   - After setting the environment variable, you can run a Docker command like `docker pull` or `docker push` to ensure Docker checks image signatures.
     ```bash
     docker pull <image_name>
     ```
   - If Docker Content Trust is enabled and the image is **not signed**, the pull operation will fail.

---

### 🚨 Important Notes:
- **Docker Content Trust** only works when pulling or pushing images that are signed using **Notary**.
- By default, DCT is **disabled** in Docker, and images will be pulled and pushed without any signature verification unless you explicitly enable it.

---

### 🧑‍💻 Example of Using Docker Content Trust:

```bash
export DOCKER_CONTENT_TRUST=1
docker pull alpine
```

If the image `alpine` is not signed (or if the signature is invalid), Docker will fail to pull it and show an error.

---

## SAMPLE QUESTION : How can you enable Docker Content Trust (DCT) in Docker Community Edition (CE)?
```
1. Set the CONTENT_TRUST environment variable to 1.
2. Pass the --content-trust flag to dockerd.
3. Set "content-trust": true in /etc/docker/daemon.json.
4. Set the DOCKER_CONTENT_TRUST environment variable to 1.
```
The correct answer is:

> ✅ **Set the DOCKER_CONTENT_TRUST environment variable to 1.**

---

### Explanation of Each Option:

#### ✅ **"Set the DOCKER_CONTENT_TRUST environment variable to 1."**
- **Correct.**
- To enable Docker Content Trust (DCT), you need to set the environment variable `DOCKER_CONTENT_TRUST=1`. This ensures that Docker will only allow pulling or pushing signed images.
  
    Example:
    ```bash
    export DOCKER_CONTENT_TRUST=1
    ```

#### ❌ **"Set the CONTENT_TRUST environment variable to 1."**
- **Incorrect.**
- The correct environment variable name is `DOCKER_CONTENT_TRUST`, not `CONTENT_TRUST`.

#### ❌ **"Pass the --content-trust flag to dockerd."**
- **Incorrect.**
- There is no `--content-trust` flag for `dockerd`. The correct method to enable Docker Content Trust is through the `DOCKER_CONTENT_TRUST` environment variable.

#### ❌ **"Set 'content-trust': true in /etc/docker/daemon.json."**
- **Incorrect.**
- Docker Content Trust cannot be enabled through the `daemon.json` configuration file. It is enabled via the `DOCKER_CONTENT_TRUST` environment variable at the user or session level.
