# Configuring Docker Daemon to Start on Boot

## Overview
Ensuring that the Docker daemon starts automatically on boot is essential for maintaining uptime and availability of containerized applications. Docker provides built-in support for system initialization using systemd, SysVinit, and other init systems.

## 1. Enable Docker to Start on Boot

### Using systemd (Linux Distributions: Ubuntu, CentOS, Debian, Fedora)
1. Check if Docker is running:
   ```sh
   systemctl status docker
   ```
2. Enable Docker to start on boot:
   ```sh
   sudo systemctl enable docker
   ```
3. Start Docker immediately:
   ```sh
   sudo systemctl start docker
   ```
4. Verify that Docker is enabled to start on boot:
   ```sh
   systemctl is-enabled docker
   ```

### Using SysVinit (Older Linux Distributions)
1. Enable Docker on startup:
   ```sh
   sudo chkconfig docker on
   ```
2. Start Docker:
   ```sh
   sudo service docker start
   ```
3. Check the status:
   ```sh
   sudo service docker status
   ```

## 2. Configuring Docker Daemon Options
Docker daemon options can be configured using the **daemon.json** file.
1. Open or create the configuration file:
   ```sh
   sudo nano /etc/docker/daemon.json
   ```
2. Add or modify the following JSON configuration:
   ```json
   {
       "log-driver": "json-file",
       "storage-driver": "overlay2",
       "bip": "192.168.1.1/24"
   }
   ```
3. Save the file and restart Docker:
   ```sh
   sudo systemctl restart docker
   ```

## 3. Verifying Docker Startup
1. Reboot the system:
   ```sh
   sudo reboot
   ```
2. After rebooting, check if Docker is running:
   ```sh
   systemctl status docker
   ```

## 4. Documentation Links
- [Docker Daemon Configuration](https://docs.docker.com/config/daemon/)
- [Docker Service Management](https://docs.docker.com/engine/reference/commandline/systemctl/)
- [Systemd Docker Management](https://docs.docker.com/config/daemon/systemd/)

## Conclusion
By enabling Docker to start on boot, administrators ensure the availability of containerized applications across reboots. Configuring the Docker daemon using `daemon.json` provides further customization for optimal performance.
