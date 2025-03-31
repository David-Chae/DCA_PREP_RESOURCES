## Which of the following statements concerning secrets is NOT correct? 
1. Secrets are encrypted during transit and also at rest.
2. Secrets are available to swarm services and  standalone containers.
3. Secrets are mounted in the container’s filesystem directly.
4. Secrets can be used for storing username and password

# Docker Secrets - Correct and Incorrect Statements

## Incorrect Statement:

❌ **"Secrets are available to swarm services and standalone containers"**

## Explanation:
Docker **secrets** are designed **only for Docker Swarm services**, not standalone containers. They provide a **secure way to store and manage sensitive data**, such as **passwords, API keys, and TLS certificates**.

---

## Why the Other Statements Are Correct:

✔ **Secrets are encrypted during transit and also at rest** ✅  
   - Docker secrets are **encrypted when stored** in the Swarm's Raft log and **encrypted in transit** between nodes.

✔ **Secrets are mounted in the container’s filesystem directly** ✅  
   - When a secret is assigned to a service, it is **mounted as a file in `/run/secrets/`** inside the container.

✔ **Secrets can be used for storing username and password** ✅  
   - Secrets are commonly used for storing **credentials**, API keys, and other sensitive information.

---

## Why the Incorrect Statement is Wrong:

❌ **"Secrets are available to swarm services and standalone containers"**  
   - **Secrets are only available to Swarm services**, not to **standalone** containers (`docker run`).  
   - Standalone containers **cannot access secrets** because secrets are managed by the **Swarm manager** and securely distributed **only to Swarm nodes** running the service.

---

## Summary:
If you need secrets in standalone containers, you must use **environment variables** or **mounted files**, but these methods are less secure than Docker Swarm secrets.
