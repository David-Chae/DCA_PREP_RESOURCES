## 18. Which commands should be used to add a label to a Docker Swarm node?
```sh
A. docker node update --label-add < label> <node name>  
B. docker node update --labels <label> <node name>  
C docker label add <label> <node name>  
D. docker node tag <label> <node name>  
```

The correct answer is:  

**A. `docker node update --label-add <label> <node name>`**  

### Explanation:  
To add a label to a Docker Swarm node, you use the `docker node update` command with the `--label-add` option.

Example:  
```sh
docker node update --label-add environment=production <node_name>
```  
This command adds a label (`environment=production`) to the specified node (`<node_name>`).

### Why the other options are incorrect:  
- **B. `docker node update --labels <label> <node name>`** → **Incorrect**  
  - The correct option uses `--label-add` rather than `--labels`. The latter does not exist in this context.

- **C. `docker label add <label> <node name>`** → **Incorrect**  
  - There is no `docker label add` command in Docker. The correct command is `docker node update`.

- **D. `docker node tag <label> <node name>`** → **Incorrect**  
  - There is no `docker node tag` command. The correct command is `docker node update`.

Thus, **A** is the correct answer.
