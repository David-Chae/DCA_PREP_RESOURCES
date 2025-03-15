## We have seven Swarm manager nodes in total. How should we distribute them across just three availability zones? 
1. 5-1-1
2. 6-1-0
3. 4-2-1
4. 3-2-2

The best way to distribute **seven Swarm manager nodes** across **three availability zones** is:  

✅ **3-2-2**  

### **Explanation:**  
- **Docker Swarm uses Raft consensus**, which requires a majority (quorum) of managers to be available for the cluster to function.  
- With **seven** managers, a majority means at least **four nodes must be available** to maintain quorum.  
- **Distributing nodes as 3-2-2** ensures that losing a single availability zone **does not bring down the cluster** because:  
  - If **one AZ fails**, at least **five nodes remain**, maintaining a quorum.  
  - If **two AZs fail**, at most **three nodes remain**, breaking quorum, but that would happen with any distribution.  

### **Why the Other Options Are Less Optimal:**  
❌ **5-1-1:**  
- If the AZ with **five nodes** fails, only **two nodes remain**, which is **not enough for a quorum** (minimum needed: 4).  

❌ **6-1-0:**  
- The AZ with **six nodes** is a **single point of failure**—if it goes down, only **one node remains**, and the cluster **fails**.  

❌ **4-2-1:**  
- Better than **5-1-1**, but still risky. If the **zone with four nodes** fails, only **three remain**, which is **not enough for quorum**.  

### **Conclusion:**  
✅ **3-2-2** is the best distribution to maintain high availability and resilience.
