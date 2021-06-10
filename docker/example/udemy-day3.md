```
vim Dcoekrfile

# Dockerfileがあるディレクトリに移動
docker build .
docker images
# 上のコマンドで作ったのイメージはダングリングの状態をdanglingになる
docker images -f dangling=true

docker build -t {tagu_name} 
```
# 基本的なインストラクション　
- FROM
  - ベースのイメージを選定し、DockerfileはFROMから始まる
  - https://hub.docker.com/_/alpine
  - centosやubuntuが約70MBに対して「alpine」は5MBと小さい
- RUN 
- CMD
- COPY

# レイヤーを小さくする
- 必要に応じて「 && 」で繋げる
- バックスラッシュで改行する

# Dockerfileの編集後のbuildにキャッシュを利用して時間短縮
- Dockerfile作成時のキャッシュ
