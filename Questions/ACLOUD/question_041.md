## Which of the following statements about Docker image vulnerability scanning is accurate?
```
1. Image vulnerability scanning inspects images before they're running on a host.
2. We need a Docker Enterprise Edition (EE) license to scan images within our registry.
3. Docker Enterprise Edition (EE) will prevent you from running images that contain vulnerabilities.
4. Docker Trusted Registry (DTR) will scan all images by default.
```

Let’s evaluate each statement to determine which is accurate regarding **Docker image vulnerability scanning**:

---

### ✅ **Correct Answer:**
> **Image vulnerability scanning inspects images before they're running on a host.**  
**✔️ True**

- Vulnerability scanning works **on static images**, **before** they are deployed as containers.
- This helps catch known vulnerabilities in packages or layers **before runtime**.

---

### ❌ **We need a Docker Enterprise Edition (EE) license to scan images within our registry.**  
**False**

- Docker EE (or its successor in Mirantis) **includes** image scanning features through **Docker Trusted Registry (DTR)**.
- However, **basic image scanning** can also be integrated using **open-source tools** like **Trivy**, **Clair**, or **Docker Hub's integrated scanning**, which don't require Docker EE.

---

### ❌ **Docker Enterprise Edition (EE) will prevent you from running images that contain vulnerabilities.**  
**False**

- Docker EE **can alert or warn** about vulnerabilities, but it **does not block image execution by default**.
- Policy enforcement (e.g., preventing deployment) would require **manual configuration** or third-party tools.

---

### ❌ **Docker Trusted Registry (DTR) will scan all images by default.**  
**False**

- DTR can scan images, but **automatic scanning needs to be enabled**.
- It does **not scan all images by default** — you can configure which repositories to scan and how often.

---

### ✅ Summary Table:

| Statement                                                                                       | True/False | Reason                                                                                   |
|--------------------------------------------------------------------------------------------------|------------|------------------------------------------------------------------------------------------|
| Image vulnerability scanning inspects images before they're running on a host.                 | ✔️ True     | Scanning is static and happens before deployment.                                        |
| We need a Docker EE license to scan images within our registry.                                | ❌ False    | EE includes scanning, but scanning can be done with other tools without EE.             |
| Docker EE will prevent you from running images that contain vulnerabilities.                   | ❌ False    | EE alerts, but doesn't block images unless you configure policy enforcement.            |
| DTR will scan all images by default.                                                           | ❌ False    | Scanning must be configured — not enabled for all images by default.                    |

Let me know if you'd like a walkthrough of how to scan Docker images using Trivy or DTR!
