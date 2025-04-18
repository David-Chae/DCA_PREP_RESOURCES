## Which flag in Docker Inspect enables us to return particular fields?
A. --filter  
B.--field-limit  
C.--pretty  
D.--format  

The correct answer is:

**D. `--format`**

### Explanation:

The `--format` flag in `docker inspect` allows you to **return specific fields** using Go templating syntax.

#### Example:
```bash
docker inspect --format='{{.Name}}' my_container
```
This command will return only the container's name instead of the entire JSON output.

### Other options explained:
- **A. `--filter`** – Used with `docker ps`, `docker images`, etc., to filter results, but **not valid for `docker inspect`**.
- **B. `--field-limit`** – ❌ Not a valid Docker CLI flag.
- **C. `--pretty`** – While `docker inspect` outputs nicely formatted JSON by default, there's **no `--pretty`** flag.

✅ **Correct answer: `D. --format`**

Let me know if you want help crafting format templates!
