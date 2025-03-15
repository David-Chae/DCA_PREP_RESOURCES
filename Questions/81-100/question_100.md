## 100. Which of the following commands can add an image tag?
A. <registry_host<:registry_port>/>repository<:tag>  
B. <registry_host<:private-ip-address>/>repository<:tag>  
C. <registry_host<:public-ip-address>/>repository<:tag>  
D. <registry_port<:registry_host>/>repository<:tag>  

The correct answer is:

**A. `<registry_host>:<registry_port>/repository:<tag>`**

### **Explanation:**

To add or assign a tag to an image, the correct format involves specifying the registry host (and optionally the port), followed by the repository name, and then the tag.

Here's what the components mean:

1. **`<registry_host>`**: This is the address of the Docker registry (it can be a public registry like Docker Hub or a private registry).
2. **`<registry_port>`**: The port of the Docker registry. The default is usually 5000 for a private registry, but many public registries don't require this.
3. **`<repository>`**: The name of the repository where the image is stored.
4. **`<tag>`**: The version or tag of the image (e.g., `latest` or `v1.0`).

Thus, the format `docker tag <image> <registry_host>:<registry_port>/repository:<tag>` is the right way to add a tag to an image.

---

### **Final Answer:**
**A. `<registry_host>:<registry_port>/repository:<tag>`**
