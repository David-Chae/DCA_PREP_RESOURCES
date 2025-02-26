Question 1  
What is the difference between the ADD and COPY Dockerfile instructions? (Choose two.)  

A. ADD supports regular expression handling while COPY does not.  
B. COPY supports compression format handling while ADD does not.  
C. ADD supports compression format handling while COPY does not.  
D. COPY supports regular expression handling while ADD does not.  
E. ADD supports remote URL handling while COPY does not.  

Answer : CE  
The main differences between the ADD and COPY instructions in a Dockerfile are:  
Compression Format Handling: ADD can automatically extract compressed files (like .tar, .gz, etc.) while COPY does not handle compression formats.  
Remote URL Handling: ADD can handle remote URLs, allowing you to add files from a URL, whereas COPY only works with local files and directories.  
So, the correct answers are:  
C. ADD supports compression format handling while COPY does not.  
E. ADD supports remote URL handling while COPY does not.  


Question 2 ( Exam A )
When an application being managed by UCP fails, you would like a summary of all requests made to the UCP API in the hours leading up to the failure.  
What must be configured correctly beforehand for this to be possible?  

A. UCP audit logs must be set to the ‘metadata’ or ‘request’ level.  
B. All engines in the cluster must have their log driver set to the ‘metadata’ or ‘request’ level.  
C. UCP logging levels must be set to the ‘info’ or ‘debug’ level.  
D. Set the logging level in the config object for the ucp-kube-api-server container to warning or higher.  

Answer : A  
To ensure you can get a summary of all requests made to the UCP API in the hours leading up to a failure, you need to configure the UCP audit logs to the 'metadata' or 'request' level12. This setting captures the necessary details about the API requests. So, the correct answer is A. UCP audit logs must be set to the ‘metadata’ or ‘request’ level.  


Question 3 ( Exam A )  
A user’s attempts to set the system time from inside a Docker container are unsuccessful.  
Could this be blocking this operation?  
SELinux  

A. Yes  
B. No  

Answer : A  
Yes, SELinux could be blocking this operation. SELinux enforces strict access controls, and by default, containers are restricted from modifying certain system settings, including the system time12.
So, the correct answer is A. Yes.


Question 4 ( Exam A )  
One of several containers in a pod is marked as unhealthy after failing its livenessProbe many times.  
Is this the action taken by the orchestrator to fix the unhealthy container?  
The unhealthy container is restarted.  

A. Yes  
B. No  

Answer : A  

Yes, when a container in a pod fails its livenessProbe multiple times, the Kubernetes orchestrator will attempt to fix the issue by restarting the unhealthy container12.
So, the correct answer is A. Yes.


Question 5 ( Exam A )  
Is this a way to configure the Docker engine to use a registry without a trusted TLS certificate?  
Set INSECURE_REGISTRY in the ‘/etc/docker/default’ configuration file.  

A. Yes  
B. No  

Answer : B  
No, setting INSECURE_REGISTRY in the /etc/docker/default configuration file is not the correct way to configure the Docker engine to use a registry without a trusted TLS certificate.  

The correct way to do this is by modifying the Docker daemon configuration file, typically located at /etc/docker/daemon.json, and adding the registry URL under the insecure-registries key12. Here is an example configuration:  

{  
  "insecure-registries": ["your-registry-domain:port"]  
}  
After making this change, you need to restart the Docker daemon for the changes to take effect.  

So, the correct answer is B. No. 

Question 6 ( Exam A )  
Is this a way to configure the Docker engine to use a registry without a trusted TLS certificate?  
Set and export the IGNORE_TLS environment variable on the command line.  

A. Yes  
B. No  

Answer : B  


Question 7 ( Exam A )  
Is this a way to configure the Docker engine to use a registry without a trusted TLS certificate?  
Pass the ‘--insecure-registry’ flag to the daemon at run time.  

A. Yes  
B. No  

Answer : A  
Yes, passing the --insecure-registry flag to the Docker daemon at runtime is a valid way to configure the Docker engine to use a registry without a trusted TLS certificate12. This flag can be added to the Docker daemon's startup options.  
So, the correct answer is A. Yes.  

Question 8 ( Exam A )  
Is this an advantage of multi-stage builds?  
better logical separation of Dockerfile instructions for increased readability  

A. Yes  
B. No  

Answer : A  
A. Yes
Multi-stage builds in Docker do indeed offer better logical separation of Dockerfile instructions, which can lead to increased readability. This approach allows you to break down your Dockerfile into multiple stages, making it easier to manage and understand.


Question 9 ( Exam A )  
Is this an advantage of multi-stage builds?  
better caching when building Docker images  

A. Yes  
B. No  


Answer : B  
B. No

While multi-stage builds offer many advantages, better caching when building Docker images is not typically one of them. The primary benefits of multi-stage builds include reducing the size of the final image and improving the readability and maintainability of Dockerfiles.


Question 9 ( Exam A )
You add a new user to the engineering organization in DTR.  
Will this action grant them read/write access to the engineering/api repository?  
Add the user directly to the list of users with read/write access under the repository’s Permissions tab.  

A. Yes  
B. No  


Answer : A  
A. Yes

Adding the user directly to the list of users with read/write access under the repository’s Permissions tab will grant them the necessary access to the engineering/api repository12.



Question 11 ( Exam A )
You add a new user to the engineering organization in DTR.
Will this action grant them read/write access to the engineering/api repository?
Mirror the engineering/api repository to one of the user’s own private repositories.

A. Yes
B. No


Question 12 ( Exam A )
You add a new user to the engineering organization in DTR.
Will this action grant them read/write access to the engineering/api repository?
Add them to a team in the engineering organization that has read/write access to the engineering/api repository.

A. Yes
B. No

Question 13 ( Exam A )
Seven managers are in a swarm cluster.
Is this how should they be distributed across three datacenters or availability zones?
3-2-2

A. Yes
B. No

In this case, a 3-2-2 distribution is acceptable because it maintains an odd number of managers (7), which helps in achieving quorum. So, the correct answer should be A. Yes.

Question 14 ( Exam A )
Seven managers are in a swarm cluster.
Is this how should they be distributed across three datacenters or availability zones?
5-1-1

A. Yes
B. No



Question 15 ( Exam A )
Is this a function of UCP?
image role-based access control

A. Yes
B. No

A. Yes
Universal Control Plane (UCP) includes role-based access control (RBAC), which allows you to manage permissions for Docker images and other resources12. This feature helps ensure that only authorized users can access and modify specific resources within your Docker environment.


Question 16 ( Exam A )
Is this a function of UCP?
enforces the deployment of signed images to the cluster

A. Yes
B. No

A. Yes
Universal Control Plane (UCP) can enforce the deployment of signed images to the cluster. This feature ensures that only trusted, signed images are used, enhancing the security and integrity of your Docker environment1


Question 17 ( Exam A )
Is this the purpose of Docker Content Trust?
Enable mutual TLS between the Docker client and server.

A. Yes
B. No

B. No
The purpose of Docker Content Trust (DCT) is to ensure the integrity and authenticity of Docker images by using digital signatures. This allows users to verify that the images they pull or deploy originate from trusted sources12. Enabling mutual TLS between the Docker client and server is not a function of Docker Content Trust.


Question 18 ( Exam A )
Is this the purpose of Docker Content Trust?
Sign and verify image tags.

A. Yes
B. No

A. Yes
The purpose of Docker Content Trust (DCT) is to sign and verify image tags. This ensures that the images you use are from trusted sources and have not been tampered with.


Question 19 ( Exam A )
Is this the purpose of Docker Content Trust?
Indicate an image on Docker Hub is an official image.

A. Yes
B. No

ANSWER:
B. No
The purpose of Docker Content Trust (DCT) is to sign and verify image tags to ensure the integrity and authenticity of Docker images. It does not specifically indicate whether an image on Docker Hub is an official image.


Question 20 ( Exam A )
In the context of a swarm mode cluster, does this describe a node? an instance of the Docker CLI connected to the swarm

A. Yes
B. No

B. No
In the context of a Docker Swarm mode cluster, a node is not defined as an instance of the Docker CLI connected to the swarm. Instead, a node refers to a physical or virtual machine running Docker Engine that is part of the swarm. Nodes can be either manager nodes, which handle cluster management tasks, or worker nodes, which execute containers.


Question 21 ( Exam A )
In the context of a swarm mode cluster, does this describe a node? a virtual machine participating in the swarm

A. Yes
B. No

ANSWER:
A. Yes
In the context of a Docker Swarm mode cluster, a node can indeed be a virtual machine participating in the swarm. Nodes in a swarm can be either physical or virtual machines running Docker Engine

Question 22 ( Exam A )
Is this a supported user authentication method for Universal Control Plane?
SAML

A. Yes
B. No

A. Yes
Universal Control Plane (UCP) supports SAML (Security Assertion Markup Language) as a user authentication method12. This allows for single sign-on (SSO) and integration with identity providers that use SAML.

Question 23 ( Exam A )
Is this a supported user authentication method for Universal Control Plane?
X.500

A. Yes
B. No

B. No
Universal Control Plane (UCP) does not support X.500 as a user authentication method. UCP supports other methods such as LDAP, SAML, and OAuth for user authentication.



Question 24 ( Exam A )
Is this statement correct?
A Dockerfile provides instructions for building a Docker image.

A. Yes
B. No

A. Yes
A Dockerfile indeed provides instructions for building a Docker image. It contains a series of commands and configurations that Docker uses to assemble an image.


Question 25 ( Exam A )
Is this statement correct?
A Dockerfile stores persistent data between deployments of a container.

A. Yes
B. No

B. No
A Dockerfile does not store persistent data between deployments of a container. Instead, it provides instructions for building a Docker image. Persistent data should be managed using volumes or external storage solutions.
