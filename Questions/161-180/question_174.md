## 174. As a stack, the following Docker Compose file is deployed:
version: "3.1'  
services:  
app:  
image: app :1.0  
healthcheck  
test:"curl --fail https://localhost/health  
|| exit 1"  
interval: 10s  
timeout: 5s  
retries: 3  

Is the given solution remark about the definition of a health check correct?  
Solution. App health checks should be done every ten seconds. Three failed health checks put the container in the "unhealthy" category  
A. Yes  
B. No  
