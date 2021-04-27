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
kubectl exec -it  nginx-${XXXXX} -- curl  ${ClusterIP}/8080
kubectl delete pod nginx-${XXXXX}
kubectl get pod
```
