- フロントエンドの外部IPを取得してcurlを実行してフロントエンドを操作する
```
kubectl get services frontend
curl -ks https://<EXTERNAL-IP>

# 上の処理を１行で行う場合
curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`
```
