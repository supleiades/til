## フロントエンドの外部 IP を取得して curl を実行し、フロントエンドを操作
```
kubectl get services frontend
curl -ks https://<EXTERNAL-IP>
 
# curl を 1 行で実行することもできます
curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`
```

## Replicatin Controllerを表示
- deployment
```
kubectl get deploy
```
