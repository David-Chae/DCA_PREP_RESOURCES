## UBUNTU Docker Installation

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# Install the latest Docker packages.
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Install specific version
# List the available versions:
apt-cache madison docker-ce | awk '{ print $3 }'

5:28.0.4-1~ubuntu.24.04~noble
5:28.0.3-1~ubuntu.24.04~noble
...

VERSION_STRING=5:28.0.4-1~ubuntu.24.04~noble
sudo apt-get install docker-ce=$VERSION_STRING docker-ce-cli=$VERSION_STRING containerd.io docker-buildx-plugin docker-compose-plugin


# Verify that the installation is successful by running the hello-world image:
sudo docker run hello-world
```

***Receiving errors when trying to run without root?***
***The docker user group exists but contains no users, which is why you’re required to use sudo to run Docker commands. Continue to Linux postinstall to allow non-privileged users to run Docker commands and for other optional configuration steps.***

To add a user to the `docker` group in **Ubuntu**, follow these steps:

---

### 🧑‍💻 Step-by-step Guide

1. **Create the `docker` group** (if it doesn't already exist):

```bash
sudo groupadd docker
```

> ⚠️ If the group already exists, this will do nothing.

---

2. **Add your user to the `docker` group**:

```bash
sudo usermod -aG docker $USER
```

> Replace `$USER` with the actual username if you're doing this for another user:
>  
> ```bash
> sudo usermod -aG docker username
> ```

---

3. **Apply the new group membership**:

Either **log out and back in** or use this command to apply changes:

```bash
newgrp docker
```

---

4. **Test the permission** (no `sudo` needed):

```bash
docker run hello-world
```

You should see the standard success message from Docker 🎉

---

### ✅ Done!

Let me know if you want a quick check script to verify group membership or troubleshoot permissions.
