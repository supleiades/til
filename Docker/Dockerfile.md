- コンテナ起動後の初期設定を記述することができる

## docker imageの元になるファイル作成
```
#Dockerfile
FROM centos:latest

RUN yum install -y git nodejs npm
```

## docker imageを作成する
```
docker build -t centos:git .
```

##作成したdocker imageの情報確認
```
docker images
> REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
> centos              test                d04f5cbd1bce        24 seconds ago      409MB
```
