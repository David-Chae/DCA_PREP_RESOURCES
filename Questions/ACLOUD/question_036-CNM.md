## What concept in the Docker Container Network Model (CNM) refers to an isolated unit containing all networking components associated with a single container?

In the Docker Container Network Model (CNM), the concept that refers to **an isolated unit containing all networking components associated with a single container** is called a **Sandbox**.

---

### ✅ **Correct Answer: `Sandbox`**

### 🔍 Explanation:

In CNM, the **Sandbox** is responsible for:

- Holding the container’s network configuration, such as:
  - IP address
  - MAC address
  - Routing table
  - DNS settings
- Providing network isolation for the container
- Managing the network stack for the container

Each container has **exactly one Sandbox**, which may be connected to one or more **Endpoints**, which in turn connect to **Networks**.

---

### 📚 CNM Key Concepts Recap:

- **Network**: A collection of endpoints that can communicate with each other.
- **Endpoint**: A virtual interface that connects a sandbox to a network.
- **Sandbox**: The container’s network stack—everything related to its networking.
- **Driver**: Plugin used to implement network functionality (bridge, overlay, etc.).

Let me know if you'd like a visual or analogy to help make this even clearer!
