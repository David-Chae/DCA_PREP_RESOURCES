
# Troubleshooting Docker Installation Issues
Understanding error messages can help diagnose and resolve common Docker installation issues.

### Common Errors and Solutions
#### 1. **Docker Daemon Not Running**
- **Error:** `Cannot connect to the Docker daemon at unix:///var/run/docker.sock`
- **Solution:**
  ```sh
  sudo systemctl start docker
  sudo systemctl enable docker
  ```
  Verify the status:
  ```sh
  sudo systemctl status docker
  ```

#### 2. **Permission Denied When Running Docker**
- **Error:** `Got permission denied while trying to connect to the Docker daemon socket`
- **Solution:**
  ```sh
  sudo usermod -aG docker $USER
  newgrp docker
  ```
  Log out and back in for changes to take effect.

#### 3. **Missing Dependencies**
- **Error:** `package docker-ce is not available`
- **Solution:** Ensure that the correct repository is added:
  ```sh
  sudo apt update
  sudo apt install docker-ce docker-ce-cli containerd.io
  ```

#### 4. **Port Conflicts**
- **Error:** `Error starting userland proxy: listen tcp 0.0.0.0:80: bind: address already in use`
- **Solution:** Identify and free up the port:
  ```sh
  sudo lsof -i :80
  sudo kill -9 <PID>
  ```
  Alternatively, start the container on a different port:
  ```sh
docker run -p 8080:80 my_container
  ```

#### 5. **Storage Issues**
- **Error:** `no space left on device`
- **Solution:** Clear unused images and containers:
  ```sh
  docker system prune -a
  ```
  Verify disk usage:
  ```sh
  df -h
  ```

## 5. Documentation Links
- [Docker Troubleshooting Guide](https://docs.docker.com/config/daemon/systemd/)
