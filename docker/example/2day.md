```
vim Dcoekrfile

# Dockerfileがあるディレクトリに移動
docker build .
docker images
# 上のコマンドで作ったのイメージはダングリングの状態をdanglingになる
docker images -f dangling=true

docker build -t {tagu_name} .
```
