## Multi-Pod Kubernetes Application
- Running the Multi-Pod Application in Kubernetes cluster. 
- This application is for learning purpose only.
- The demo is for deploying wordpress application and mysql database with persistent volume.
- The secret file has username and password for mysql database that will be used to connnect with wordpress site. Use base64decoder to decode the value in text format.

**Order of file to be executed**
```
kubectl create -f mysql_pvc.yml 

kubectl create -f secret.yml  

kubectl create -f mysql_pvc_pod.yml  

kubectl create -f mysql_service.yml

kubectl create -f wp_pvc.yml  

kubectl create -f wp_pvc_pod.yml  

kubectl create -f wp_service.yml 
```