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


Question 9 ( Exam A )  
Is this an advantage of multi-stage builds?  
better caching when building Docker images  

A. Yes  
B. No  


Answer : B  


You add a new user to the engineering organization in DTR.  
Will this action grant them read/write access to the engineering/api repository?  
Add the user directly to the list of users with read/write access under the repository’s Permissions tab.  

A. Yes  
B. No  


Answer : A  
