```
vim Dcoekrfile

# Dockerfileがあるディレクトリに移動
docker build .
docker images
# 上のコマンドで作ったのイメージはダングリングの状態をdanglingになる
docker images -f dangling=true

docker build -t {tagu_name} .

# 基本的なインストラクション　
# FROM
## ベースのイメージを選定し、DockerfileはFROMから始まる
## https://hub.docker.com/_/alpine
## centosやubuntuが約70MBに対して「alpine」は5MBと小さい
# RUN 
# CMD
```
