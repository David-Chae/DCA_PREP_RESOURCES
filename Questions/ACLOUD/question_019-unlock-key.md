## Kelly has a Docker swarm cluster with --autolock enabled. One of her manager nodes has become locked, and she has lost the unlock key. Fortunately, there are still some swarm nodes that are not locked. How can she obtain the unlock key from one of the unlocked nodes?

You're absolutely right! My apologies for the confusion. In fact, Docker **does not store the unlock key in a plain file** like `/etc/docker/swarm/unlock.key`. Here's the correct approach:

### Correct Solution:
If **Kelly has lost the unlock key** for a manager node with **auto-lock enabled** and there are still unlocked manager nodes available in the swarm, she can retrieve the unlock key using the following approach:

1. **Access an Unlocked Manager Node**:
   - If there are **other manager nodes** in the Swarm cluster that are still **unlocked**, she can obtain the unlock key from one of them.

2. **Use the Docker CLI to Retrieve the Key**:
   - On an **unlocked manager node**, Kelly can run the following command to retrieve the unlock key:
     ```bash
     docker swarm unlock-key
     ```

   This will output the unlock key that she can then use to unlock the locked manager node.

---

### Why the other options are incorrect:

- **`docker swarm key print`**: This is not a valid command in Docker. There is no command for directly printing the unlock key.

- **`docker swarm unlock`**: This command is used to unlock the node, but it requires the unlock key to proceed. If Kelly has lost the key, this command won't be helpful until she retrieves the key.

- **`/etc/docker/swarm/unlock.key`**: As you rightly pointed out, Docker does not store the unlock key in a file like `/etc/docker/swarm/unlock.key`. The unlock key is generated dynamically and only available through the `docker swarm unlock-key` command when the node is unlocked.

---

### ✅ Recap:
Kelly should run the following on an **unlocked manager node** to retrieve the unlock key:
```bash
docker swarm unlock-key
```

Once she has the key, she can use it to unlock the locked manager node with:
```bash
docker swarm unlock
```

Thanks for pointing that out, and let me know if you have further questions!
