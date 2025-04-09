## What are valid methods that we can use for setting the default DNS server for all containers on a host?

---

## ✅ 1. **Edit `/etc/docker/daemon.json`** (Preferred & Persistent)
As previously mentioned:
```json
{
  "dns": ["8.8.8.8", "1.1.1.1"]
}
```
- **Affects all containers created after the change**
- **Persistent** across reboots
- Requires Docker daemon restart: `sudo systemctl restart docker`

---

## ✅ 2. **Start Docker daemon with `--dns` flag**
If you're not using `daemon.json`, you can also modify the **systemd unit file**:

1. Edit Docker service file override:
   ```bash
   sudo systemctl edit docker
   ```

2. Add:
   ```ini
   [Service]
   ExecStart=
   ExecStart=/usr/bin/dockerd --dns 8.8.8.8 --dns 1.1.1.1
   ```

3. Reload systemd and restart Docker:
   ```bash
   sudo systemctl daemon-reexec
   sudo systemctl restart docker
   ```

> 📝 This method is useful if you want to keep everything in systemd overrides rather than JSON.

---

## ✅ 3. **Custom Docker bridge network with default DNS**
You can create a **custom bridge network** with a DNS server set, and run containers on that:

```bash
docker network create \
  --driver bridge \
  --dns 8.8.8.8 \
  custom-net
```

Then run containers like:
```bash
docker run --rm --network custom-net alpine cat /etc/resolv.conf
```

- This **does not affect the default bridge network**
- Good for scoped control (e.g., per-project DNS settings)

---

## ✅ 4. **Configure DNS at container run-time (manual per container)**
Using `--dns` on `docker run`:
```bash
docker run --dns 8.8.8.8 alpine
```

- **Manual** and **not default for all containers**
- Useful for testing or special cases

---

## ✅ 5. **Use Docker Compose with DNS configured**
In a `docker-compose.yml` file:

```yaml
services:
  web:
    image: nginx
    dns:
      - 8.8.8.8
      - 1.1.1.1
```

- Scope is per service or per app stack
- Not global, but good in CI/CD or dev environments

---

### 🔚 Summary Table

| Method                         | Scope                 | Persistent? | Applies Globally? |
|-------------------------------|------------------------|-------------|--------------------|
| `daemon.json`                 | All containers         | ✅          | ✅                 |
| Systemd `--dns` override      | All containers         | ✅          | ✅                 |
| Custom bridge network         | Containers using it    | ✅          | ❌                 |
| `--dns` on `docker run`       | Single container       | ❌          | ❌                 |
| Compose file `dns:`           | Per service            | ✅          | ❌                 |

---

## SAMPLE QUESTION : Which of the following is a valid method that we can use for setting the default DNS server for all containers on a host?

```
1. We can use docker config set dns.
2. We can set "dns" in /etc/docker/daemon.json.
3. We can edit the /etc/hosts file on the host.
4. We can use the --dns flag with docker run.
```

The **correct answer** is:

> ✅ **We can set `"dns"` in `/etc/docker/daemon.json`.**

---

### 🔍 Explanation of Each Option:

#### ❌ **"We can use `docker config set dns`."**
- **Incorrect.**  
There is **no** such Docker command as `docker config set dns`.  
You might be thinking of `docker config`, which is used for **Swarm configs**, not for DNS settings.

---

#### ✅ **"We can set `"dns"` in `/etc/docker/daemon.json`."**
- **Correct.**  
This is the **standard and persistent** way to set default DNS for all containers on a Docker host.

Example:
```json
{
  "dns": ["8.8.8.8", "1.1.1.1"]
}
```
Then restart Docker:
```bash
sudo systemctl restart docker
```

---

#### ❌ **"We can edit the `/etc/hosts` file on the host."**
- **Incorrect.**  
The host’s `/etc/hosts` file does **not affect** container DNS resolution.  
Each container has its own `/etc/hosts` and `/etc/resolv.conf`.

---

#### ❌ **"We can use the `--dns` flag with `docker run`."**
- **Technically correct**, but **not a method to set the default for all containers**.  
It sets DNS **only for that specific container** at run time.

Example:
```bash
docker run --dns 8.8.8.8 alpine
```
But you'd have to do this **every time**, which doesn’t qualify as a **default for all containers**.

---

### ✅ Final Answer:
> **We can set `"dns"` in `/etc/docker/daemon.json`.**

