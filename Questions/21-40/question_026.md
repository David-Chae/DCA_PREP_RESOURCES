## What procedure should we follow to upgrade the Docker engine on an Ubuntu server? 
1. Remove all containers, stop Docker, and then install the newer version. 
2. Stop Docker, then install the packages with the newer version. 
3. Stop Docker, remove the packages, and then reinstall the packages with a newer version. 
4. Install newer versions of the docker-ce and docker-ce-cli packages.

The correct procedure to upgrade the Docker engine on an Ubuntu server is:

**Install newer versions of the `docker-ce` and `docker-ce-cli` packages.**

### **Steps:**
1. **Update the apt package index:**
   ```bash
   sudo apt-get update
   ```

2. **Install the latest version of Docker:**
   ```bash
   sudo apt-get install --only-upgrade docker-ce docker-ce-cli
   ```

   This will upgrade the Docker Engine and CLI to the latest version available in the Docker repository.

3. **Restart Docker service:**
   ```bash
   sudo systemctl restart docker
   ```

### **Explanation:**
- Docker packages (`docker-ce` and `docker-ce-cli`) can be directly upgraded by running the above commands without needing to remove containers, stop Docker, or reinstall packages.
- Docker's package management system ensures that the newer versions are installed when upgrading using the `apt` package manager on Ubuntu.
