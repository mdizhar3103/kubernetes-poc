## Working with Kubernetes 
- This repo contains the files to work with kubernetes by deploying simple django based python application.
- The repo also contain the files to deploy multi-pod wordpress and mysql application in multi-container-app folder.
- There is also a file for working with deployment.

**Deploying the Pod and Creating the Service**
```
kubectl apply -f pod-app.yml

kubectl apply -f app-service.yml
```

***Note:*** In application the developer has restricted the IP addresses to serve the application to specific users and you might not be able to see it as running when you try accessing via web browser. To avoid that use the following command to allow all IP's to connect to that application.

```
# entering inside pod 
kubectl exec -it djangoa-app -- sh

# going to application directory
cd /Django-Application/Django-Project-1/pyshop

# editing setting file (use insert mode by pressing 'I' since we are using vi editor)
vi settings.py 
Look for ALLOWED_HOST = ['0.0.0.0', '192.168.43.49'] and modify it as:

ALLOWED_HOST = ['*', '0.0.0.0', '192.168.43.49']
Now save and close the file, and re run on browser you will be able to access the application now. 
```


**Creating the Deployment of same application**
```
kubectl apply -f deployment-app.yml

# Playing with deployment - Scaling, Rolling back, Rolling out, etc
kubectl get deployments

kubectl describe deployment django-app-deployment

kubectl get deployment/django-app-deployment -o yaml

kubectl scale deployment/django-app-deployment --replicas=5

kubectl delete pod/django-app-deployment-

kubectl get replicaset

kubectl rollout history deployment/django-app-deployment

kubectl rollout pause deployment/django-app-deployment

kubectl set resources deployment/django-app-deployment -c="django-deploy" --limits=cpu=200m,memory=512Mi

kubectl rollout resume deployment/django-app-deployment

kubectl get pods

kubectl rollout status deployment/django-app-deployment

kubectl rollout history deployment/django-app-deployment

kubectl get deployments

kubectl describe deployments

kubectl rollout undo deployment/django-app-deployment
# or
kubectl rollout undo deployment/django-app-deployment --to-revision=2

kubectl get deployments
```

