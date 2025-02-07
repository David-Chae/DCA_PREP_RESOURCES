### Steps to Lock a Docker Swarm Cluster

Locking a Docker Swarm cluster ensures that its cryptographic keys are encrypted, preventing unauthorized access. Follow these steps:

#### **1. Initialize the Swarm (If Not Already Initialized)**
If your swarm is not yet initialized, run:
```sh
docker swarm init
```
This sets up the node as a swarm manager.

#### **2. Enable Swarm Autolock**
To enable swarm autolock, run:
```sh
docker swarm update --autolock=true
```
This ensures that the swarm manager will require an unlock key whenever it restarts.

#### **3. Retrieve the Unlock Key**
Once autolock is enabled, Docker generates an unlock key. To retrieve it, run:
```sh
docker swarm unlock-key
```
Example output:
```
SWM_KEY-1-abcdefgh1234567890
```
Save this key securely, as you will need it to unlock the swarm after a manager node restart.

#### **4. Restart the Manager Node**
If a manager node is restarted, it will require manual unlocking.

#### **5. Unlock the Swarm**
After restarting a manager node, unlock the swarm using:
```sh
docker swarm unlock
```
When prompted, enter the unlock key.

#### **6. Disable Autolock (If Needed)**
To disable autolock, run:
```sh
docker swarm update --autolock=false
```

---

### **Relevant Official Documentation:**
- [Docker Swarm Security](https://docs.docker.com/engine/swarm/how-swarm-mode-works/security/)
- [Swarm Autolock](https://docs.docker.com/engine/reference/commandline/swarm_unlock/)
- [Lock your swarm to protect its encryption key](https://docs.docker.com/engine/swarm/swarm_manager_locking/)

### **Asciinema Examples:**
- [Demonstrate steps to lock a swarm cluster](https://asciinema.org/a/224518)
