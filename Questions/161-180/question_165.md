## 165. You wish to inspect the events table for this object while troubleshooting a Kubernetes deployment called api. Does the given command display it? kubectl events deployment api
A. Yes  
B. No  

The correct answer is:

**B. No**

Explanation:
The correct command to inspect events for a specific Kubernetes object, such as a deployment, is:

```bash
kubectl get events --field-selector involvedObject.name=api
```

or 

```bash
kubectl describe deployment api
```

The command `kubectl events deployment api` is incorrect because `kubectl events` is not a valid command. Instead, you use `kubectl get events` to list the events, and you can filter or describe specific events related to a deployment using the appropriate field selectors or describe command.
