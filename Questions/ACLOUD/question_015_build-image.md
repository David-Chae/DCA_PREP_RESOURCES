## How can I build an image from a Dockerfile located in the current directory and tag it as my-custom-image:1 ?

To build a Docker image from a `Dockerfile` located in the current directory and tag it as `my-custom-image:1`, use the following command:

```bash
docker build -t my-custom-image:1 .
```

### Explanation:
- `docker build`: Command to build a Docker image.
- `-t my-custom-image:1`: Tags the image with the name `my-custom-image` and tag `1`.
- `.`: Specifies the build context, in this case the current directory (`.`), which should contain the `Dockerfile`.
---

Q: Which of the following commands will build an image from a Dockerfile located in the current directory and tag it as my-custom-image:1?
```
docker build -tag my-custom-image:1 .
docker build -tag my-custom-image:1
docker build .
docker build -t my-custom-image:1 .
```

The **correct command** is:

```
docker build -t my-custom-image:1 .
```

### Here's why the others are incorrect or incomplete:

1. ❌ `docker build -tag my-custom-image:1 .`  
   - Incorrect: The correct flag is `-t`, not `-tag`.

2. ❌ `docker build -tag my-custom-image:1`  
   - Incorrect: Same issue as above (`-tag` is invalid), and it's also missing the build context (`.`).

3. ⚠️ `docker build .`  
   - Valid syntax, but it **doesn't tag** the image, so it won't be named `my-custom-image:1`.

✅ So, the only correct option is:
```
docker build -t my-custom-image:1 .
```
