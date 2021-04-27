```
vim deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  labels:
    app: nginx
    name: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - image: nginx
        name: nginx


kubectl apply -f deployment.yaml

kubectl get pod

# ３つのうち1つのpodを消してみても新しいnameで３つ起動しているように見える
kubectl delete pod nginx-${XXXXX}

kubectl get pod
```
