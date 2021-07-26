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

## 作成したdocker imageの情報確認
```
docker images
> REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
> centos              test                d04f5cbd1bce        24 seconds ago      409MB
```

## DockerFileの命令
|命令|説明|
|:-|:-|
|FROM|ベースイメージの指定|
|RUN|コマンド実行|
|CMD|コンテナの実行コマンド|
|LABEL|ラベルを設定|
|EXPOSE|ポートのエクスポート|
|ENV|環境変数|
|ADD|ファイル/ディレクトリ の追|
|COPY|ファイルのコピー|
|VOLUME|ボリュームのマウント|
|ENTRYPOINT|コンテナの実行コマンド|
|USER|ユーザーの指定|
|WORKDIR|作業ディレクトリ |
|ONBUILD|ビルド完了時に実行される命令|
|STOPSIGNAL|コンテナ終了時に送信するシグナル|

## link
- https://docs.docker.jp/engine/reference/builder.html#id2
