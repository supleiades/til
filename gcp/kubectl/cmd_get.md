# コマンドの出力を引数に使う
- kubectl get svc frontend
```md
NAME       TYPE           CLUSTER-IP       EXTERNAL-IP     PORT(S)         AGE
frontend   LoadBalancer   10.115.254.178   34.122.227.64   443:31849/TCP   2m15s
```
- kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"
```md
34.122.227.64
```
- IPを動的に取得してcurlコマンドを叩く
```md
curl -ks https://34.122.227.64curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`

# {"message":"Hello"}
```
