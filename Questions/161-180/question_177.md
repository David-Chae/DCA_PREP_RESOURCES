## 177. How to remove the label from the node?
A. docker node update --label-rm foo worker 1  
B. docker node update --label-rm key=foo worker1  
C. docker node update --label-rm foo worker1 worker2  
D. docker node update -label-rm key=foo worker1 worker2  

**B. docker node update --label-rm key=foo worker1**

Explanation:
The correct syntax for removing a label from a node is:

```
docker node update --label-rm key=foo worker1
```

This command removes the label `key=foo` from the node `worker1`.
