## What component of the Docker Container Networking Model (CNM) refers to a collection of endpoints that can communicate with one another?

The correct answer is:

> ✅ **A Docker network.**

---

### Explanation:

In the **Docker Container Networking Model (CNM)**, a **network** refers to a collection of **endpoints** that can communicate with each other. 

- **Endpoints** are the individual containers (or other entities like services) that are connected to a network.
- A **Docker network** allows containers connected to it to communicate with each other, either by using the container's IP address or by referencing container names (depending on the network driver in use).
  
#### Key points:
- A **Docker network** can consist of multiple containers that are able to communicate.
- Docker provides several network drivers like **bridge**, **host**, **overlay**, etc., each with different use cases.

---

