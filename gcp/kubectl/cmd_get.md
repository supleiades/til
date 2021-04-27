# コマンドの出力を引数に使う
```sh
kubectl get svc frontend
# NAME       TYPE           CLUSTER-IP       EXTERNAL-IP     PORT(S)         AGE
# frontend   LoadBalancer   10.115.254.178   34.122.227.64   443:31849/TCP   2m15s

kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"
# 34.122.227.64

# IPを動的に取得してcurlコマンドを叩く
curl -ks https://34.122.227.64curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`

# {"message":"Hello"}
```


# 設定したpod数動いているかの正常確認
```md
kubectl get pods | grep hello- | wc -l
5

kubectl get deployment
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
auth       1/1     1            1           6m49s
frontend   1/1     1            1           5m54s
hello      5/5     5            5           6m3s

kubectl get pods | grep hello-
hello-687bb4b8f4-29c6h      1/1     Running   0          6m20s
hello-687bb4b8f4-2pjtt      1/1     Running   0          6m20s
hello-687bb4b8f4-6hvlr      1/1     Running   0          33s
hello-687bb4b8f4-fbl5d      1/1     Running   0          6m20s
hello-687bb4b8f4-zl9pc      1/1     Running   0          33s
```
