# Learn Kubernetes in Minikube

## Install Minikube 
### Windows installation
```
choco install minikube
```
### WSL - Ubuntu (Linux) installation
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm64
sudo install minikube-linux-arm64 /usr/local/bin/minikube && rm minikube-linux-arm64
```
## This repository contain below YAML file
1. Secret file           : secret.yaml
                           (Manually create as code provided below, rename the user and password using base64)       
2. config                : mongo-config.yaml
3. Deployment & Service  : mongo-app.yaml
                           (replicate 1)
4. Web Application       : web-app.yaml
                           (replicate 3)
                           Add nodePort : 30200  in webapp.yaml (permission access from outside of pod) 

## Create secret.yaml with below code
Replace mongo-user and mongo-password with base64 value.
```
apiVersion: v1
kind: Secret
metadata:
  name: mongo-secret
type: Opaque
data:
  mongo-user : [base64 value]
  mongo-password : [base64 value]
```

## Docker commands
- Check docker version      : ```docker version```
- Check container           : ```docker ps -a```
  
## Minikube commands
- Check minikube version    : ```minikube version```
- Start minikube            : ```minikube start```
- Check Minikube status     : ```minikube status```
- Check Minikube IP         : ```minikube ip```
- Launch Minikube Dashboard : ```minikube dashboard```
- Launch webapp-service     : ```minikube service webapp-service```
- Launch mongo-service      : ```minikube service mongo-service```

## Kubernetes Cluster Commands
- Check Kubernetes version  : ```kubectl version```
- List all pod              : ```kubectl get pod```
- List all pod widw         : ```kubectl get pod -o wide```
- List secret               : ```kubectl get secret ```
- List all ConfigMap        : ```kubectl get configmap```
- List all Service          : ```kubectl get svc```

## Apply YAML files into kubernetes
- kubectl apply -f secret.yaml
- kubectl apply -f mongo-config.yaml
- kubectl apply -f mongo-app.yaml
- kubectl apply -f web-app.yaml

## Troubleshooting pods deployment error
```
kubectl get pods --all-namespaces
kubectl describe pod  <pods> -n <namespace>
```

## Clean up
- Delete deployment       : ```kubectl delete deployment --all```
- Delete service          : ```kubectl delete service --all ```
- Delete secret           : ```kubectl delete secret --all ```
- Delete configmap        : ```kubectl delete configmap --all```
- Delete minikube         : ```docker rm -f minikube```
