## Which of the following statements about Docker image vulnerability scanning is accurate? 
1. Image vulnerability scanning inspects images before they are running on a host.
2. Docker Enterprise Edition (EE) will prevent you from running images that contain vulnerabilities.
3. We need a Docker Enterprise Edition (EE) license to scan images within our registry.
4. Docker Trusted Registry (DTR) will scan all images by default.


The correct answer is:  

✅ **"Image vulnerability scanning inspects images before they are running on a host."**  

### **Explanation:**
- **Docker image vulnerability scanning** is a process that examines **container images** for known security vulnerabilities **before they are deployed** and run.
- This helps identify and mitigate security risks early in the software development lifecycle.

### **Why the Other Options Are Incorrect:**
1. **"Docker Enterprise Edition (EE) will prevent you from running images that contain vulnerabilities."**  
   ❌ **Incorrect**: Docker EE **does not automatically block** vulnerable images. It **alerts users** about vulnerabilities, but the decision to run or block the image depends on security policies and configurations.

2. **"We need a Docker Enterprise Edition (EE) license to scan images within our registry."**  
   ❌ **Partially true but misleading**:  
   - Docker **Enterprise Edition (EE)** provides **built-in security scanning** via **Docker Trusted Registry (DTR)**.
   - However, **third-party tools** (like **Trivy, Clair, or Snyk**) can also scan images **without** requiring Docker EE.

3. **"Docker Trusted Registry (DTR) will scan all images by default."**  
   ❌ **Incorrect**:  
   - **DTR can scan images**, but it **does not scan them by default**.  
   - Image scanning must be **enabled manually**, and policies can be configured to define when scanning occurs.

### **Final Answer:**  
✅ **"Image vulnerability scanning inspects images before they are running on a host."**
