```sh
# nginxイメージのダウンロード
# run 実行時に ローカル環境にイメージがなければイメージのダウンロードも一緒に行われる。
# nginxコンテナ実行
docker run -d -p 8080:80  nginx

# コンテナ内のnginxへのHTTPリクエストによる挙動確認
curl 127.0.0.1:8080

# コンテナの削除
# -f をつけることでstopしなくても削除可能となる
# -f をつけない場合、稼働中のコンテナは削除できない。
docker container rm -f  ${Container ID}

# nginx イメージの削除の確認
docker image rm -f nginx
```
