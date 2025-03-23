## 195. Your company uses a centralized logging solution like Splunk
## Will the given set up a Docker container to send container logs to the logging solution?
In the daemon. json file, set the log-driver and log-opt keys to values for the logging solution (Splunk).
A. Yes
B. No

**A. Yes**

By setting the `log-driver` and `log-opt` keys in the `daemon.json` file to the appropriate values for the Splunk logging solution, you can configure the Docker engine to send container logs to Splunk. This is a valid method for directing Docker logs to a centralized logging solution like Splunk.
