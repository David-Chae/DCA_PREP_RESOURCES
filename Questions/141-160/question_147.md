147. Which of the following connects the container to the network bridge?
```sh
A. --bridge string
B. --ip IP
C. --icc
D. All of the above
```

Let's break down each option to understand which one connects the container to the network bridge:

- **A. --bridge string**: This option is used to specify the bridge network to which the container should be connected. However, this isn't a valid flag in Docker commands. The correct flag for connecting a container to a specific bridge network would be `--network bridge` or similar.

- **B. --ip IP**: This option allows you to assign a specific IP address to a container within a particular network. It doesn't directly connect the container to the network bridge, but it assigns a static IP within a given network.

- **C. --icc**: This stands for "Inter-container communication." This flag controls whether containers can communicate with each other. While it affects communication between containers, it doesn't directly connect a container to a network bridge.

- **D. All of the above**: Since none of the previous options directly connects the container to a network bridge (and they each serve different functions), this answer is incorrect.

### Correct Answer:
None of the provided answers are entirely correct for directly connecting a container to a network bridge. The correct command to connect a container to the default bridge network is usually done by simply specifying the `--network bridge` option during container creation.

So, the best response here would be to either update the question with a more appropriate set of options or clarify the functionality.
