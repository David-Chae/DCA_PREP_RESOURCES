# DCA_PREP_RESOURCES

# Exam Guide

## Table of Contents
1. Domain 1: Orchestration (25% of exam)
2. Domain 2: Image Creation, Management, and Registry (20% of exam)
3. Domain 3: Installation and Configuration (15% of exam)
4. Domain 4: Networking (15% of exam)
5. Domain 5: Security (15% of exam)
6. Domain 6: Storage and Volumes (10% of exam)

## Domain 1: Orchestration (25% of exam)
Content may include the following:
- [Complete the setup of a swarm mode cluster with managers and worker nodes](Domain_1_Orchestration/Complete_the_setup_of_a_swarm_mode_cluster_with_managers_and_worker_nodes.md)
- [State the differences between running a container vs running a service](Domain_1_Orchestration/State_the_differences_between_running_a_container_vs_running_a_service.md)
- [Demonstrate steps to lock a swarm cluster](Domain_1_Orchestration/Demonstrate_steps_to_lock_a_swarm_cluster.md)
- [Extend the instructions to run individual containers into running services under swarm](Domain_1_Orchestration/Extend_the_instructions_to_run_individual_containers_into_running_services_under_swarm.md)
- [Interpret the output of docker inspect commands](Domain_1_Orchestration/Interpret_the_output_of_docker_inspect_commands.md)
- [Convert an application deployment into a stack file using a YAML compose file with docker stack deploy](Domain_1_Orchestration/Convert_an_application_deployment_into_a_stack_file_using_a_YAML_compose_file_with_docker_stack_deploy.md)
- [Manipulate a running stack of services](Domain_1_Orchestration/Manipulate_a_running_stack_of_services.md)
- [Increase number of replicas](Domain_1_Orchestration/Increase_number_of_replicas.md)
- [Add networks, publish ports](Domain_1_Orchestration/Add_networks_publish_ports.md)
- [Mount volumes](Domain_1_Orchestration/Mount_volumes.md)
- [Illustrate running a replicated vs global service](Domain_1_Orchestration/Illustrate_running_a_replicated_vs_global_service.md)
- [Identify the steps needed to troubleshoot a service not deploying](Domain_1_Orchestration/Identify_the_steps_needed_to_troubleshoot_a_service_not_deploying.md)
- [Apply node labels to demonstrate placement of tasks](Domain_1_Orchestration/Apply_node_labels_to_demonstrate_placement_of_tasks.md)
- [Sketch how a Dockerized application communicates with legacy systems](Domain_1_Orchestration/Sketch_how_a_Dockerized_application_communicates_with_legacy_systems.md)
- [Paraphrase the importance of quorum in a swarm cluster](Domain_1_Orchestration/Paraphrase_the_importance_of_quorum_in_a_swarm_cluster.md)
- [Demonstrate the usage of templates with docker service create](Domain_1_Orchestration/Demonstrate_the_usage_of_templates_with_docker_service_create.md)

## Domain 2: Image Creation, Management, and Registry (20% of exam)
Content may include the following:
- Describe Dockerfile options
- Show the main parts of a Dockerfile
- Give examples on how to create an efficient image via a Dockerfile
- Use CLI commands such as list delete prune rmi etc to manage images
- Inspect images and report specific attributes using filter and format
- Demonstrate tagging an image
- Utilize a registry to store an image
- Display layers of a Docker image
- Apply a file to create a Docker image
- Modify an image to a single layer
- Describe how image layers work
- Deploy a registry
- Configure a registry
- Log into a registry
- Utilize search in a registry
- Tag an image
- Push an image to a registry
- Sign an image in a registry
- Pull an image from a registry
- Describe how image deletion works
- Delete an image from a registry

## Domain 3: Installation and Configuration (15% of exam)
Content may include the following:
- Demonstrate the ability to upgrade the Docker engine
- Complete setup of repo select a storage driver and complete installation of Docker engine on multiple platforms
- Configure logging drivers
- Setup swarm, configure managers, add nodes, and setup backup schedule
- Create and manage user and teams
- Interpret errors to troubleshoot installation issues without assistance
- Outline the sizing requirements prior to installation
- Understand namespaces cgroups and configuration of certificates
- Use certificate-based client-server authentication to ensure a Docker daemon has the rights to access images on a registry
- Consistently repeat steps to deploy Docker engine UCP and DTR on AWS and on premises in an HA config
- Complete configuration of backups for UCP and DTR
- Configure the Docker daemon to start on boot

## Domain 4: Networking (15% of exam)
Content may include the following:
- Create a Docker bridge network for a developer to use for their containers
- Troubleshoot container and engine logs to understand a connectivity issue between containers
- Publish a port so that an application is accessible externally
- Identify which IP and port a container is externally accessible on
- Describe the different types and use cases for the built-in network drivers
- Understand the Container Network Model and how it interfaces with the Docker engine and network and IPAM drivers
- Configure Docker to use external DNS
- Use Docker to load balance HTTP HTTPs traffic to an application (Configure L7 load balancing with Docker EE)
- Understand and describe the types of traffic that flow between the Docker engine registry and UCP controllers
- Deploy a service on a Docker overlay network
- Describe the difference between host and ingress port publishing mode

## Domain 5: Security (15% of exam)
Content may include the following:
- Describe the process of signing an image
- Demonstrate that an image passes a security scan
- Enable Docker Content Trust
- Configure RBAC in UCP
- Integrate UCP with LDAP AD
- Demonstrate creation of UCP client bundles
- Describe default engine security
- Describe swarm default security
- Describe MTLS
- Identify roles
- Describe the difference between UCP workers and managers
- Describe process to use external certificates with UCP and DTR

## Domain 6: Storage and Volumes (10% of exam)
Content may include the following:
- State which graph driver should be used on which OS
- Demonstrate how to configure devicemapper
- Compare object storage to block storage and explain which one is preferable when available
- Summarize how an application is composed of layers and where those layers reside on the filesystem
- Describe how volumes are used with Docker for persistent storage
- Identify the steps you would take to clean up unused images on a filesystem also on DTR
- Demonstrate how storage can be used across cluster nodes

