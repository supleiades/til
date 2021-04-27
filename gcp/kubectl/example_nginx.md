- nginxを作ってから消す
```
vim pod.yaml

apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    app: nginx
    name: nginx
spec:
  containers:
  - image: nginx
    name: nginx


kubectl apply -f pod.yaml

kubectl get pod

kubectl delete pod nginx

kubectl get pod
```
