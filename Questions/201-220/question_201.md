## 201. Will the given procedure entirely erase an image from the Docker Trusted Registry's disk?
## Remove the image from the Docker Trusted Registry and the image repository.
A. Yes  
B. No  



**201.Answer: B**
Explanation: Deleting the image and deleting the image repository from the Docker Trusted Registry will not remove the image entirely from the disk.
To recoup disk space, you must additionally execute trash collection on the Docker Trusted Registry, ac-
cording to the official instructions.
Reference:
https://docs.docker.com/ee/dtr/admin/manage-images/garbage-collection/
