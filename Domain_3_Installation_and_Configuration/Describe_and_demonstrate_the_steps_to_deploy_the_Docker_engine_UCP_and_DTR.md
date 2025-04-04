# Deploying Docker Engine, UCP, and DTR in HA Configuration on AWS and On-Premises

## Overview
This guide outlines the steps required to deploy Docker Engine, Docker Universal Control Plane (UCP), and Docker Trusted Registry (DTR) in a High Availability (HA) configuration on both AWS and on-premises environments.

## Prerequisites
- **AWS Requirements:**
  - AWS account with IAM permissions to create EC2 instances, security groups, and load balancers.
  - VPC with private and public subnets.
  - AWS CLI installed and configured.
- **On-Premises Requirements:**
  - Physical or virtual machines with supported OS (Ubuntu, RHEL, or CentOS preferred).
  - Networking configured for HA deployment (e.g., Load Balancer, private network access).
  - Required ports opened for UCP and DTR communication.

## Step 1: Install Docker Engine
### AWS Deployment
```sh
# Install dependencies
sudo apt update && sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io

# Enable and start Docker
sudo systemctl enable --now docker
```

### On-Premises Deployment
Repeat the above installation steps on all on-premises nodes.

## Step 2: Deploy Docker UCP in HA Mode
### AWS & On-Premises Deployment
```sh
# Install UCP on the first manager node
docker run --rm -it --name ucp \
  -v /var/run/docker.sock:/var/run/docker.sock \
  docker/ucp install --host-address <ManagerNodeIP> --interactive
```

Add additional manager nodes for HA:
```sh
docker run --rm -it --name ucp \
  -v /var/run/docker.sock:/var/run/docker.sock \
  docker/ucp join --host-address <NewManagerNodeIP> --interactive
```

Add worker nodes:
```sh
docker run --rm -it --name ucp \
  -v /var/run/docker.sock:/var/run/docker.sock \
  docker/ucp join --host-address <WorkerNodeIP> --interactive
```

## Step 3: Deploy Docker Trusted Registry (DTR) in HA Mode
### AWS & On-Premises Deployment
Install DTR on the first replica node:
```sh
docker run --rm -it docker/dtr install \
  --ucp-node <UCPNode> \
  --ucp-username admin \
  --ucp-url https://<UCPManagerIP> \
  --replica-id 1
```

Add additional replicas:
```sh
docker run --rm -it docker/dtr join \
  --ucp-node <NewDTRNode> \
  --ucp-username admin \
  --ucp-url https://<UCPManagerIP> \
  --replica-id <ReplicaID>
```

## Step 4: Configure Load Balancer
- **AWS:** Use an Elastic Load Balancer (ELB) to route traffic to UCP and DTR.
- **On-Premises:** Use HAProxy or NGINX as a reverse proxy.

## Step 5: Validate the Deployment
```sh
# Check UCP status
docker container logs ucp

# Check DTR status
docker container logs dtr
```

## Official Documentation
- Docker Engine: [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)
- Docker UCP: [https://docs.mirantis.com/ucp/current/](https://docs.mirantis.com/ucp/current/)
- Docker DTR: [https://docs.mirantis.com/dtr/current/](https://docs.mirantis.com/dtr/current/)

This guide provides a high-level overview of deploying Docker Engine, UCP, and DTR in an HA setup. Refer to the official documentation for more details and troubleshooting tips.
