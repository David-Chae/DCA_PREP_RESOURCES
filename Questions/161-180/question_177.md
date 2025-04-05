## 177. How to remove the label from the node?
A. docker node update --label-rm foo worker 1  
B. docker node update --label-rm key=foo worker1  
C. docker node update --label-rm foo worker1 worker2  
D. docker node update -label-rm key=foo worker1 worker2  

**B. docker node update --label-rm key=foo worker1**

✅ **Correct Answer: B. docker node update --label-rm key=foo worker1**

---

### 📘 **Explanation:**

To **remove a label** from a Docker node, the correct syntax for the command is:

```bash
docker node update --label-rm key=foo worker1
```

Where:
- `--label-rm` is used to **remove the label**.
- `key=foo` is the label key-value pair you want to remove (`key` is the label name, and `foo` is the value).
- `worker1` is the **node name** from which the label is to be removed.

---

### ❌ Why the other options are incorrect:

- **Option A:** `docker node update --label-rm foo worker 1`  
  - This is incorrect because it doesn't properly specify the label format. Labels must follow the `key=value` syntax.

- **Option C:** `docker node update --label-rm foo worker1 worker2`  
  - This is incorrect because the label removal should apply to a **single key-value pair**. The command should not attempt to remove the label from multiple nodes in a single operation using this syntax.

- **Option D:** `docker node update -label-rm key=foo worker1 worker2`  
  - This option is incorrect because the flag `-label-rm` is invalid (it should be `--label-rm` with two dashes). Also, the correct syntax requires specifying the label as `key=value`.

---

### ✅ **Final Answer: B. docker node update --label-rm key=foo worker1**
