## Which of the following scenarios would still allow the quorum to complete maintenance in a swarm cluster? (Choose two)

```
1. A 7-node cluster with 3 nodes down.
2. A 3-node cluster with 1 node down.
3. A 4-node cluster with 2 nodes down.
4. A 3-node cluster with 2 nodes down.
```


Let’s evaluate each scenario based on Docker Swarm's **quorum requirement**, which means **a majority of manager nodes** (more than half) must be available for the cluster to function and complete tasks like **scheduling, leader election, or maintenance**.

---

### ✅ **Correct Answers:**
- **A 7-node cluster with 3 nodes down**  
  ✔️ **True** – 4 out of 7 nodes are still up → **majority present**, quorum is maintained.

- **A 3-node cluster with 1 node down**  
  ✔️ **True** – 2 out of 3 nodes are up → **majority present**, quorum is maintained.

---

### ❌ Incorrect Answers:
- **A 4-node cluster with 2 nodes down**  
  ❌ **False** – Only 2 of 4 nodes remain. That’s **exactly half**, **not a majority**, so quorum is **lost**.

- **A 3-node cluster with 2 nodes down**  
  ❌ **False** – Only 1 node is up → definitely **no majority**, **quorum is lost**.

---

### 📌 Rule of Thumb:
> For quorum, **(N/2) + 1 manager nodes** must be healthy and communicating, where N is the number of managers.

Let me know if you'd like a visual of how quorum plays out across different cluster sizes!
