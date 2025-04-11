## How would we go about keeping track of changes made to an image in source control (i.e., git)?
```
1.Maintain tags for each new version within the Docker registry.
2. We would store the Dockerfile in source control.
3. We would push the image layers to a source control repository.
4. We would use Docker Trusted Registry (DTR) to handle this.
```

✅ **Correct answer:**  
**We would store the Dockerfile in source control.**

---

### ✅ Explanation:

The **Dockerfile** is a text file that defines how to build a Docker image. By storing it (and any supporting files like scripts or configuration files) in a version control system like **Git**, you can:

- Track changes over time  
- Reproduce builds reliably  
- Collaborate with team members  
- Roll back to previous versions

---

### ❌ Why the other options are incorrect:

- **"Maintain tags for each new version within the Docker registry"**  
  🔸 Tags help manage versions **within the registry**, but they’re not connected to **source control** and don’t track how the image was built.

- **"We would push the image layers to a source control repository"**  
  ❌ Docker image layers are binary data and not suitable for Git. Git is meant for **text-based source code** and not large binary blobs.

- **"We would use Docker Trusted Registry (DTR) to handle this."**  
  🔸 DTR helps with secure image distribution and scanning, but it’s not a **source control system**.

---

Let me know if you'd like help designing a Git workflow for Docker projects!
