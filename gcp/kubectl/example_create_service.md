# type: ClusterIP
- クラスター内からこのIPに通信が飛ぶと、ラベル「nginx」を持ったポッドへTCP80の通信が行われる
```
vim clusterIP-svc.yaml

apiVersion: v1
kind: Service
metadata:
  labels:
    app: nginx
  name: nginx
spec:
  type: ClusterIP
  ports:
  - port: 8080
    protocol: TCP
    targetPort: 80
  selector:
    app: nginx


kubectl apply -f clusterIP-svc.yaml
kubectl get service

# [-it]の後のポッドから[--]の後に指定したコマンドを送信する
kubectl exec -it  nginx-${XXXXX} -- curl  ${ClusterIP}/8080

kubectl delete pod nginx-${XXXXX}
kubectl get pod
```

#type: NodePort
```
vim nodeport-svc.yaml

apiVersion: v1
kind: Service
metadata:
  labels:
    app: nginx
  name: nginx-nodeport
spec:
  type: NodePort
  ports:
  - port: 8080
    protocol: TCP
    targetPort: 80
    nodePort: 30080
  selector:
    app: nginx



kubectl apply -f nodeport-svc.yaml
gcloud compute firewall-rules create all-allow --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=all --source-ranges=0.0.0.0/0
kubectl get node -owide
curl 34.71.171.147:30080

```

# type: LoadBalancer
```
vim lb-svc.yaml

apiVersion: v1
kind: Service
metadata:
  labels:
    app: nginx
  name: nginx-lb
spec:
  type: LoadBalancer
  ports:
  - port: 8080
    protocol: TCP
    targetPort: 80
  selector:        
    app: nginx


kubectl apply -f lb-svc.yaml
kubectl get service  
curl ${type LBの サービスのIP}:8080
```
