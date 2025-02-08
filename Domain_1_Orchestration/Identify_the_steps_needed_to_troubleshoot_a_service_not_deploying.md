# Troubleshooting a Service Not Deploying in Docker Swarm

If a service is not deploying in Docker Swarm, follow these steps to diagnose and resolve the issue.

---

## 1. Check Service Status

Use the following command to inspect the service state:

```sh
docker service ps my_service
```

- Look for errors in the `Desired State` and `Current State` columns.
- If tasks are failing or restarting, investigate further.

---

## 2. Inspect the Service Logs

View logs to check for errors:

```sh
docker service logs my_service
```

- Look for crash loops, permission errors, or networking issues.

---

## 3. Verify Node Availability

Ensure that Swarm nodes are active and ready:

```sh
docker node ls
```

- If nodes are `Down` or `Unreachable`, check network connectivity and restart the affected nodes.

---

## 4. Check Image Availability

Ensure that the container image exists and can be pulled:

```sh
docker pull my_image
```

- If the image is missing, check the repository or registry access.

---

## 5. Inspect Network and Ports

Ensure the correct network is being used:

```sh
docker network ls
```

- If a custom network is required, verify its setup.
- Ensure that ports are available and not in use by another service.

---

## 6. Debug Task Failures

Check failed tasks for details:

```sh
docker inspect $(docker ps -q --filter "name=my_service")
```

- Look for error messages in the container logs.

---

## 7. Restart the Service

Try restarting the service:

```sh
docker service update --force my_service
```

- This forces a redeployment of the service.

---

## 8. Check Docker Daemon Logs

If issues persist, check Docker daemon logs on the nodes:

```sh
journalctl -u docker.service --no-pager | tail -n 50
```

- Look for system-level errors.

---

## References

- [Docker Swarm Troubleshooting Guide](https://docs.docker.com/engine/swarm/troubleshoot/)
- [Pending services](https://docs.docker.com/engine/swarm/how-swarm-mode-works/services/#pending-services)
- [How do I find out why my Docker service is in Pending state?](https://stackoverflow.com/questions/41641380/how-do-i-find-out-why-my-docker-service-is-in-pending-state/41658522#41658522)
- [Identify the steps needed to troubleshoot a service not deploying](https://asciinema.org/a/224933)
