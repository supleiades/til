# expose
- クラスタ外のインターネット アドレスから nginx ポッドへのアクセスを許可する LoadBalancer Service が作成
```
kubectl expose pod $my_nginx_pod --port 80 --type LoadBalancer
```
