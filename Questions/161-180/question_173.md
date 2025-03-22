## 173. Your company uses a centralized logging solution like Splunk.
## Will the given command set up a Docker container to send container logs to the logging solution?
docker logs  
A. Yes  
B. No  

The correct answer is:

**B. No**

Explanation:
The `docker logs` command is used to view logs of a specific container, not to configure a container to send logs to a centralized logging solution like Splunk. To send logs from Docker containers to an external logging system like Splunk, you need to configure a logging driver (e.g., `syslog`, `fluentd`, or `splunk`) when running the container using the `--log-driver` flag, like so:

```bash
docker run --log-driver=splunk ...
```

This ensures that the container logs are forwarded to the centralized logging solution.
