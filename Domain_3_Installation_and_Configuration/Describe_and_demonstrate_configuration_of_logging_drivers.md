# Configuring Logging Drivers in Docker

## Overview
Docker provides multiple logging drivers that allow container logs to be collected, stored, and forwarded to various logging systems. Some commonly used logging drivers include:

- `json-file` (default)
- `journald`
- `syslog`
- `splunk`
- `fluentd`
- `awslogs`

## Configuring Logging Drivers
Docker logging drivers can be set either:
- Per-container
- Globally (daemon-level)

### 1. Setting a Logging Driver for a Container
To configure a logging driver for an individual container, use the `--log-driver` flag when running the container.

#### Example: Using `journald` Logging Driver
```sh
docker run --log-driver=journald --name mycontainer alpine echo "Hello, journald!"
```

#### Example: Using `splunk` Logging Driver
```sh
docker run --log-driver=splunk \
  --log-opt splunk-token="your-splunk-token" \
  --log-opt splunk-url="https://splunk-server:8088" \
  --log-opt splunk-insecureskipverify=true \
  --name mycontainer alpine echo "Hello, Splunk!"
```

### 2. Setting a Global Logging Driver
To configure a logging driver for all containers, modify the Docker daemon configuration file.

1. Open or create the `/etc/docker/daemon.json` file:
```sh
sudo nano /etc/docker/daemon.json
```
2. Add the following configuration:

#### Example: Using `journald`
```json
{
  "log-driver": "journald"
}
```

#### Example: Using `splunk`
```json
{
  "log-driver": "splunk",
  "log-opts": {
    "splunk-token": "your-splunk-token",
    "splunk-url": "https://splunk-server:8088",
    "splunk-insecureskipverify": "true"
  }
}
```

3. Restart Docker to apply changes:
```sh
sudo systemctl restart docker
```

## Verifying Logs
To verify logs collected by the logging driver:
- **journald**: Use `journalctl`
  ```sh
  journalctl -u docker.service --no-pager
  ```
- **splunk**: Check the Splunk UI or use the Splunk REST API.

## Documentation
For further details, refer to official documentation:
- Docker Logging Drivers: [https://docs.docker.com/config/containers/logging/](https://docs.docker.com/config/containers/logging/)
- Splunk Logging Driver: [https://docs.docker.com/config/containers/logging/splunk/](https://docs.docker.com/config/containers/logging/splunk/)
- Journald Logging Driver: [https://docs.docker.com/config/containers/logging/journald/](https://docs.docker.com/config/containers/logging/journald/)

## Conclusion
Using appropriate logging drivers ensures effective monitoring and troubleshooting of Docker containers. Choosing between `journald`, `splunk`, or other options depends on your infrastructure and operational needs.

