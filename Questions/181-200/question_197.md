## 197. You wish to inspect the events table for this object while troubleshooting a Kubernetes deployment called api. Does the following command display it?
## kubectl describes the deployment api
A. Yes  
B. No  

**B. No**

The correct command to view events related to a Kubernetes deployment would be `kubectl describe deployment api` (with `describe` instead of `describes`). However, to specifically view the events table, you would use the `kubectl get events` command.
