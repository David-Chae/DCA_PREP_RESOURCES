152. Which tag will be pulled using the docker pull command if we do not specify a tag?
```sh
A. Latest
B. Production
C. Staging
D. Master
```


The correct answer is:  
**A. Latest**

### Explanation:
When you use the `docker pull` command **without specifying a tag**, Docker **automatically defaults to the `latest` tag**.

#### Example:
```bash
docker pull ubuntu
```
This command is **equivalent to**:
```bash
docker pull ubuntu:latest
```

### Breakdown of Options:
- **A. Latest ✅** – This is the default tag used by Docker when none is specified.
- **B. Production ❌** – Not a default Docker tag; used manually in custom tagging workflows.
- **C. Staging ❌** – Also a custom tag, not used by default.
- **D. Master ❌** – More commonly seen in Git branches, not a default Docker tag.

So, unless otherwise stated, Docker assumes you want the `:latest` tag.
