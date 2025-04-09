## Where can we find a repository URL for installing the Docker Enterprise Edition (EE)?

To find the **repository URL for installing Docker Enterprise Edition (EE)**, you must go through **Docker’s official enterprise partner portal or subscription service**, as **Docker EE is a commercial product** and not openly available like Docker CE (Community Edition).

---

### ✅ Here’s how to get the Docker EE repository URL:

#### 1. **Visit Docker’s official enterprise portal:**
- Go to: [https://www.mirantis.com/software/docker/docker-enterprise/](https://www.mirantis.com/software/docker/docker-enterprise/)
  > Mirantis now maintains Docker EE after acquiring Docker Enterprise in 2019.

#### 2. **Sign in or request a trial:**
- You'll need a **Mirantis (Docker Enterprise) subscription** to access the repositories.
- After logging in, you'll be given **custom repository URLs** for your operating system and version.

#### 3. **The repository URL is usually in this form:**
```
https://<customer_id>.docker.com/repo/ubuntu/ or /rhel/ or /centos/
```
Or:
```
https://packages.mirantis.com/<os-version>/
```

You’ll also receive credentials (username and password or token) to access private repositories.

---

### 🛑 Important Notes:
- Docker EE is not available via public package managers like `apt` or `yum` without this subscription.
- The repositories contain packages like `docker-ee`, `docker-ee-cli`, and `docker-ee-engine`.

---

### 🐳 If You Just Need Docker CE (Community Edition):
Use the official public repo:
```bash
https://download.docker.com/linux/ubuntu
```
Or:
```bash
https://download.docker.com/linux/centos
```

---

## SAMPLE QUESTION : Where can we find a repository URL for installing the Docker Enterprise Edition (EE)?
```
1. Docker Trusted Registry
2. Docker Marketplace
3. Docker Hub
4. Docker Enterprise Hub
```
