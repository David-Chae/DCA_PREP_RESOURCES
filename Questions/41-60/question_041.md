## 41.How can we use multi-stage builds to generate small, efficient Docker images?
```sh
A. We can build the image and then run diagnostics on it in a separate stage to make it more efficient
B. We can use separate build stages to delete files from the image
C. We can copy only specific files from previous stages to keep the image as small as possible.
D. We can leverage the implementation of multi-stage builds, which will shorten the build processing times.
```

The correct answer is:  

**C. We can copy only specific files from previous stages to keep the image as small as possible.**  

### Explanation:  
Multi-stage builds in Docker allow you to use multiple `FROM` statements in a `Dockerfile`, where each stage can have its own environment. This helps in:  
- Compiling or building dependencies in an intermediate stage.  
- Copying only the necessary artifacts (like compiled binaries) to the final image, reducing size.  
- Avoiding the inclusion of unnecessary files, build tools, and dependencies.  

### Why not the others?  
- **A**: Running diagnostics does not inherently make an image smaller.  
- **B**: Deleting files does not always reduce the image size since Docker images retain layers. Multi-stage builds allow avoiding unnecessary files altogether.  
- **D**: Multi-stage builds primarily reduce image size, not necessarily build time.
