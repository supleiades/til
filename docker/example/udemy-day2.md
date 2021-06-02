```sh
# -t: 表示を綺麗にする。これがないとコマンドの保管をしてくれなかったりする
# -i: strinを可能にする
## strin: キーボードからプログラムまでの入力のチャネル
## strout: プログラムからディスプレイまでの標準出力のチャネル
## strerr: プログラムからディスプレイまでのエラー出力のチャネル
docker run -it ubuntu bash

# 削除はステータス:UP状態のコンテナに実行できない
docker stop 078f79641d73
docker rm 078f79641d73# 
# 止まっているコンテナ削除、ダングリングされているイメージなどを一括削除
# ダングリング: タグ付けがされていない（<none>）
docker system prune

# docker run --name {name} ubuntu
docker run --name first-repository supleiades/first-repository


# detached modd 
## docker run -d {image}
## コンテナを起動後にdetach（バックグラウンドで動かす）

# (short-term)foreground mode
## docker run --rm {image}
## コンテナをExit後に削除する（一度きりのコンテナ）




```
