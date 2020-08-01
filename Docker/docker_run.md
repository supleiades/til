## docker imageを指定して起動
```
docker run --name test -ti centos:latest
```


## 未使用のdockerも含めて全てのdocker情報を表示
```
docker ps -a
> CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                       PORTS               NAMES
> 2bd23adae979        centos:latest       "/bin/bash"         10 hours ago        Exited (130) 10 hours ago                        test
```
