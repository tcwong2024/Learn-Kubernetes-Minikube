# Learn Kubernetes and Minikube

## Create YAML files for kubenetes cluster
- Secret                : secret.yaml
- config                : mongo-config.yaml
- Deployment & Service  : mongo-app.yaml    (replicate 1)
- Web Application       : web-app.yaml      (replicate 3)
- Add nodePort : 30200  in webapp.yaml (permission access from outside of pod) 
- Start minikube : minikube start


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
