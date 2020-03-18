# 前提条件 
anyenvがインストール済みであること


## anyenvコマンド
複数言語のパッケージを管理するツール
```
$ anyenv install --list
  Renv
  crenv
  denv
  erlenv
  exenv
  goenv
  hsenv
  jenv
  luaenv
  nodenv
  phpenv
  plenv
  pyenv
  rbenv
  sbtenv
  scalaenv
  swiftenv
  tfenv
```
インストール済みのパッケージ管理ツールとそのバージョン
```
$ anyenv versions
nodenv:
  12.16.1
  13.10.1
pyenv:
  system
* 3.8.2 
```
# 今回は言語をnode.jsを使用する例にて説明
## nodenvコマンド
anyenvで管理されているnodenvを使用
```
$ nodenv versions
  12.16.1
  13.10.1
```
インストール可能なバージョンを確認
```
$ nodenv install --list
0.1.14
0.1.15
0.1.16
0.1.17
...
iojs-3.3.1
nightly
node-dev
rc
v8-canary
```
特定のバージョンの最新版を確認
```
// var.12の最新版
$ nodenv install --list | grep -v [a-zA-Z] | grep ^12 | tail -1
12.16.1
```
```
$ node install 12.16.1
```

## プロジェクト（ディレクトリ）ごとに使用するバージョンを変える
```
$ nodenv local 10.19.0
$ nodenv version
10.19.0 
```
