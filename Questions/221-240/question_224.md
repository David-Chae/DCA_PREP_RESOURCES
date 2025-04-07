## 224. How to inspect the service on the swarm so that it will print limited information in an easily readable format?
A. docker service inspect <service> --pretty  
B. docker inspect service <service> --format="{{.Spec.Name}}"  
C. docker swarm service inspect <service> --format-="{{.Spec.Name}}" --pretty  
D. docker inspect <service> --format="{{.SpecName}}" -pretty  

The correct command to inspect a service on the swarm and print limited information in an easily readable format is:

**A. docker service inspect <service> --pretty**

Explanation:
- **A** uses the `--pretty` flag with `docker service inspect`, which provides a more human-readable format with limited and key information about the service. Reference: https://docs.docker.com/reference/cli/docker/service/inspect/

The other options are incorrect:
- **B**: `docker inspect service <service> --format="{{.Spec.Name}}"` is not a valid command as the `docker inspect` command does not use "service" in that context.
- **C**: `docker swarm service inspect <service> --format="{{.Spec.Name}}" --pretty` is incorrect as `docker swarm service inspect` is not a valid command.
- **D**: `docker inspect <service> --format="{{.Spec.Name}}" -pretty` is also incorrect due to improper formatting and the invalid use of `-pretty`.

So, the correct answer is **A**.

---

### 🔍 Now, regarding my follow-up:
> Can `docker service inspect --format="{{.Spec.Name}}" <service name>` be a valid answer?

✅ **Yes, it is a valid command**, but it’s **not the best answer** to the question as asked.

- It **doesn’t print "limited information in a readable format"** by itself — instead, it outputs **just one specific field** (in this case, the service name), and you must **specify the service name** too.
  
Example:
```bash
docker service inspect --format="{{.Spec.Name}}" nginx-web
```
This will output:
```
nginx-web
```

So yes, it’s valid Docker syntax and helpful if you're scripting or querying specific fields — but for **general human-readable inspection**, `--pretty` is more appropriate.

---

### ✅ TL;DR:
- **A** is the correct and best answer for this question.
- **`--format` is valid**, but it's **not a replacement** for `--pretty` in this context. It's more for targeted scripting.

Let me know if you want examples using both!
