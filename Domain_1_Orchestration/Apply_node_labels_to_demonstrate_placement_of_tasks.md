# Applying Node Labels in Docker Swarm

Node labels in Docker Swarm allow you to control where services are placed by defining constraints.

---

## 1. Add a Label to a Node

To add a label to a specific node, use:

```sh
docker node update --label-add mylabel=value node_id
```

- Replace `mylabel` with the desired label key.
- Replace `value` with an appropriate label value.
- Replace `node_id` with the actual node ID from `docker node ls`.

Example:

```sh
docker node update --label-add role=db worker1
```

---

## 2. Verify Labels on a Node

To check the labels assigned to a node:

```sh
docker node inspect node_id --format '{{ .Spec.Labels }}'
```

Example:

```sh
docker node inspect worker1 --format '{{ .Spec.Labels }}'
```

---

## 3. Deploy a Service with Placement Constraints

To schedule a service on nodes with a specific label:

```sh
docker service create --name my_service --constraint 'node.labels.mylabel == value' nginx
```

Example:

```sh
docker service create --name db_service --constraint 'node.labels.role == db' mysql
```

- This ensures the service only runs on nodes labeled `role=db`.

---

## 4. Remove a Node Label

To remove a label from a node:

```sh
docker node update --label-rm mylabel node_id
```

Example:

```sh
docker node update --label-rm role worker1
```

---

## References

- [Docker Node Labels Documentation](https://docs.docker.com/engine/swarm/manage-nodes/#add-or-remove-labels-on-a-node)
- [docker node update](https://docs.docker.com/reference/cli/docker/node/update/)
- [Placement constraints](https://docs.docker.com/engine/swarm/services/#placement-constraints)
- [asciinema: Apply node labels to demonstrate placement of tasks](https://asciinema.org/a/224934)
