## 242. Customizing the ingress network involves removing and creating a new one, and you need to do that before you create any services in the swarm. Is this statement correct?
A. Yes, customizing the ingress network necessitates the removal of the existing one and the creation of a new one. This should be done before creating any swarm services  
B. No, the ingress network can be customized at any time, even after services have been created in the swarm.  
C. Customizing the ingress network is impossible; it remains fixed in its configuration  
D. You can only customize the ingress network when adding new manager nodes to the swarm.  

---

## 🧠 What’s Actually True About the Ingress Network?

### 👉 Ingress Network ≠ Just Any Network
The **ingress network** is **special** because it's used for **routing mesh**, not like typical user-defined overlay networks.

---

## 🔍 Let's Reevaluate Option A:

> **A. Yes, customizing the ingress network necessitates the removal of the existing one and the creation of a new one. This should be done before creating any swarm services.**

### Why This Is **Misleading**:

- ✅ It is **true** that if you want to **customize the built-in ingress network itself** (like its subnet, IPAM configs, MTU), Docker requires it to be recreated **before** any services use it.
- ❌ But it **fails to clarify** that you can:
  - Still run services with other networks, including **custom overlay networks**, even after services exist.
  - Use `docker service update --network-add <new-network>` to **attach new networks**.
  - Avoid using the default ingress network entirely by running services in **host mode** or publishing ports in other ways.

So, **option A is incomplete** and **assumes you must use the ingress network for all services**, which isn't necessarily true.

---

## ✔️ More Accurate Rewording:

> **"The built-in ingress network can only be customized by removing and recreating it, which must happen before any services using it are running. However, services can still be attached to other networks or updated to use different ones later."**

---

## 🔚 Conclusion:
https://docs.docker.com/engine/network/drivers/overlay/#connection-limit-for-overlay-networks
