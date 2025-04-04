## 118. Which of the following commands can be used to connect the terminal?
A. docker rm  
B. docker logs  
C. docker ps  
D. docker service ls  

This question is a bit off for a DOMC question. The options listed don't align with connecting to a container or terminal, and the phrasing of the question might make it seem like it's asking about SSH, which is a separate concept.

To clarify, none of the options directly deal with connecting to a terminal of a container. Here’s a breakdown:

A. docker rm: This is used to remove a container, not connect to it.

B. docker logs: This is used to view the logs of a container.

C. docker ps: This lists running containers, but doesn’t connect to them.

D. docker service ls: This lists services in a Docker Swarm cluster, unrelated to terminal access.

If the question is about connecting to a container’s terminal, it would make more sense to ask about the docker exec or docker attach commands, which are used to interact with a running container.

For example, a more suitable question for DOMC might be:

"Which of the following commands allows you to open an interactive terminal session inside a running container?"

A. docker exec -it <container_id> bash
B. docker rm
C. docker ps
D. docker service ls

The correct answer would be A, as docker exec is used to run commands inside a container and open a terminal session.

This revised question better tests knowledge of Docker's interactive features, which would be more aligned with Docker certification-level questions.
