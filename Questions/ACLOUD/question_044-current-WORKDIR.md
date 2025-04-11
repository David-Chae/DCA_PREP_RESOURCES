What would be the runtime working directory of a container built from the following Dockerfile?
```Dockerfile
FROM alpine

WORKDIR /x
WORKDIR /y
WORKDIR z

CMD pwd
```

1. /x  
2. /y/z   
3. /
4. /z  


The correct answer is:

> ✅ **2. /y/z**

---

### ✅ Explanation:

In a Dockerfile, the `WORKDIR` directive sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions that follow it.

Each `WORKDIR` builds **on top of** the previous one if given a **relative path**.

Let's break down the Dockerfile step-by-step:

```Dockerfile
FROM alpine

WORKDIR /x     → Sets working directory to /x

WORKDIR /y     → Absolute path → sets working directory to /y

WORKDIR z      → Relative path → appends to /y → becomes /y/z

CMD pwd        → Runs `pwd` when the container starts
```

So, at runtime, the `CMD pwd` will output:

```bash
/y/z
```

---

### ❌ Why the other answers are wrong:

- **1. /x** → Overridden by `/y`
- **3. /** → Default, but overridden multiple times
- **4. /z** → Would be the case if `WORKDIR z` was used first (after `/`), but here it’s relative to `/y`

Let me know if you'd like a demo with `docker build` and `docker run` to test it!
