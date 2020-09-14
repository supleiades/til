# WSLでDockerをインストールする時に躓いたので備忘録

## 基本的な導入手順

https://qiita.com/tkyonezu/items/0f6da57eb2d823d2611d


## 躓きポイント
- 「curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -」

このコマンドを実行するとエラーが表示される
```
gpg: can't connect to the agent: IPC connect call failed
```

- 今回の解決方法は「gpgの再インストール」
```
$ sudo apt remove gpg
$ sudo apt install gnupg1
```


## 参考
- 基本的なインストール：https://qiita.com/tkyonezu/items/0f6da57eb2d823d2611d
- WSLの躓きポイント　：https://qiita.com/obukoh/items/416c4cb1b88261bf3357
