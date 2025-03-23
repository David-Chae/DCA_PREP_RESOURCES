## 190. Is it enough to have only two swarm managers, one active and one passive, to achieve fault tolerance?
A. Yes  
B. No  

**B. No**  

In Docker Swarm, fault tolerance for managers is achieved through the **Raft consensus algorithm**, which requires a **majority (quorum) of managers** to maintain cluster state consistency.  

- With **only two managers**, if one fails, the remaining single manager **cannot form a majority** (since 1 out of 2 is not a majority).  
- The recommended number of managers for fault tolerance is **at least three** (so that a majority can still be formed if one manager fails).  

Thus, having only two managers does **not** provide fault tolerance, as a failure would make the cluster **unavailable**.
