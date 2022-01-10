# roleのインストール方法
- Ansible  Galaxyのサイトにあるroleをダウンロードするためには「ansible-galaxy」コマンドを利用する
```sh
ansible-galaxy install {role名}
```

## 引数：init
- 推奨されるroleの空のディレクトリ構成を一気に作ることができる
```sh
ansible-galaxy init {role名}
```
- 実行例
```
