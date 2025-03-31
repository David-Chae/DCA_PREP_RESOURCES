## Which of the following commands can be used to see the IPv4 subnet of a network?
A. docker network 1s  
B. docker info network  
C. docker network info  
D. docker network inspect  

Here’s the analysis of each option with **true/false** and explanations:

**A. `docker network 1s`** → **False**  
- The command `docker network 1s` is incorrect because `1s` is not a valid subcommand of `docker network`. Likely, this is a typo for `docker network ls`, which lists networks but does **not** show the subnet details.

**B. `docker info network`** → **False**  
- `docker info` provides general system-wide information about Docker, but it does not have a `network` argument or display network subnets.

**C. `docker network info`** → **False**  
- `docker network info` is not a valid Docker command. There is no such subcommand.

**D. `docker network inspect`** → **True**  
- `docker network inspect <network_name>` provides detailed information about a specific network, including its **IPv4 subnet**, gateway, and connected containers.  

**Example Usage:**  
```sh
docker network inspect bridge
```
This will output details like:
```json
"IPAM": {
    "Config": [
        {
            "Subnet": "192.168.1.0/24",
            "Gateway": "192.168.1.1"
        }
    ]
}
```

### Final Answer:
- **A: False** (Invalid command)
- **B: False** (Does not exist)
- **C: False** (Not a valid command)
- **D: True** (Correct way to get subnet details)
