## How would we keep track of changes made to an image in source control (i.e., git)? 
1. We would use Docker Trusted Registry (DTR) to handle this.
2. Maintain tags for each new version within the Docker registry.
3. We would push the image layers to a source control repository.
4. We would store the Dockerfile in source control.

The correct answer is:

✅ **We would store the Dockerfile in source control.**

---

### **Explanation:**

- **Storing the Dockerfile in source control (e.g., Git)** is the best practice for tracking changes made to an image. The Dockerfile contains the instructions for building the Docker image, so keeping it in source control allows you to track changes in the image's configuration, dependencies, and setup over time.

- By versioning the Dockerfile in a repository, you can trace the exact changes that have been made to the Docker image, ensuring a transparent and reproducible build process. This is particularly useful in collaboration and CI/CD (Continuous Integration/Continuous Delivery) workflows.

---

### **Why the Other Options Are Incorrect:**

❌ **"We would use Docker Trusted Registry (DTR) to handle this."**
- Docker Trusted Registry (DTR) is useful for storing and managing Docker images in a private registry, but it does not provide version tracking or history of changes like source control (e.g., Git) does for Dockerfiles.

❌ **"Maintain tags for each new version within the Docker registry."**
- While tags help identify different versions of an image, they do not give you a detailed history of the specific changes made to the image over time. Tags are useful for versioning but do not provide the full context of what has changed inside the image.

❌ **"We would push the image layers to a source control repository."**
- Pushing image layers (i.e., the binary data representing different parts of the Docker image) to source control is inefficient and unnecessary. Source control systems like Git are designed to handle text files (like the Dockerfile), not large binary files, and this would lead to bloated repositories.

---

### **Summary:**

To keep track of changes made to an image in source control, the best approach is to store the **Dockerfile** in a Git repository. This allows for effective versioning and tracking of changes in the image's build process.
