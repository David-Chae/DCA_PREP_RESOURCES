## When building a volume alongside a service that uses docker service create, what flag should we use to define a custom volume driver?
A. --volumedriver <driver>  
B.--driver <driver>  
C. --volume-driver <driver>  
D. --mount volume-driver=<driver>  

The correct answer is:  

✔ **D. --mount volume-driver=<driver>**  

---

79. Answer: D Explanation: With the chosen driver, the custom volume will be created. Reference: https://docs.docker.com/engine/reference/commandline/service_create/
