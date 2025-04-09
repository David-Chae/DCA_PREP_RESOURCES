## In docker, what command will evenly spread out tasks based upon the values of a node label?

In Docker Swarm, to **evenly spread out tasks** across nodes **based on the values of a node label**, you can use the following constraint in combination with the **`--placement-pref`** flag when creating a service:

### ✅ Command:
```bash
docker service create \
  --name my_service \
  --replicas 6 \
  --placement-pref 'spread=node.labels.my_label' \
  my_image
```

### 🔍 Explanation:
- `--placement-pref 'spread=node.labels.my_label'` tells Docker to **spread the service's tasks across nodes** based on the value of the label `my_label`.
- This ensures that the **tasks are distributed as evenly as possible** among the nodes with different values of the specified label.

### Example:
If your nodes have these labels:

- Node 1: `node.labels.zone=us-east`
- Node 2: `node.labels.zone=us-west`
- Node 3: `node.labels.zone=us-central`

...then the tasks will be distributed across `us-east`, `us-west`, and `us-central` as evenly as possible (e.g., 2 tasks per zone for 6 replicas).

Let me know if you want to see how to **set those node labels** or inspect the task distribution after it's running!

## QUESTION : Which of the following commands will evenly spread out tasks based upon the values of a node label?
```
1. docker service create --placement-pref even-spread=node.labels.availability_zone nginx
2. docker service create --placement-pref spread nginx
3. docker service create --constraint spread=node.labels.availability_zone nginx
4. docker service create --placement-pref spread=node.labels.availability_zone nginx
```
***ANS: 4. docker service create --placement-pref spread=node.labels.availability_zone nginx***
