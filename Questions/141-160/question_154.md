## 154. _______________ layers in a Docker image corresponds to a Dockerfile instruction. Each layer is a delta of the modifications from the layer beneath it, and the layers are layered.
```sh
A. Movable
B. read-only
C. write only
D. read and write
```

The correct answer is:

**B. read-only**

Explanation:
- Each layer in a Docker image is **read-only**. When a new layer is added (e.g., from a Dockerfile instruction like `RUN`, `COPY`, or `ADD`), it is stacked on top of the previous layers, but the previous layers remain immutable and cannot be changed.

- The **read-only** nature of layers means that once a layer is created, it cannot be modified, and any changes are written to new layers on top of it. This helps ensure consistency and efficiency in the image's storage and use.
