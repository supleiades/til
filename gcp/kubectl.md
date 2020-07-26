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

## ロールアウト履歴を表示
```
kubectl rollout history deployment/
```

## ロールアウトの状確認
```
kubectl rollout status deployment/hello
```
- ポッドで直接確認することもできる
```
kubectl get pods -o jsonpath --template='{range .items[*]}{.metadata.name}{"\t"}{"\t"}{.spec.containers[0].image}{"\n"}{end}'
```


## 特定のポッドに関する詳細な情報出力（トラブルシューティングなどで役立つ）
```
kubectl describe pods {特定のpod名}
```
