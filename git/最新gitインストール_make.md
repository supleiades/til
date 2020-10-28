## 事前準備
- makeコマンドの処理などに必要なライブラリインストール
```
sudo yum -y install gcc curl-devel expat-devel gettext-devel openssl-devel zlib-devel perl-ExtUtils-MakeMaker autoconf
```

## インストール
```js
// 適当な作業ディレクトリに移動
cd /tmp


// gitの圧縮ファイルをダウンロード
// URL最後の以下で言うと[git-2.9.5.tar.gz]を任意のバージョンに変更することも可
sudo curl -OL https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz


// 圧縮ファイルを解凍
sudo tar xzvf git-2.9.5.tar.gz


// 圧縮ファイルを削除
sudo rm git-2.9.5.tar.gz


// 解凍先のディレクトリに移動
// 移動先のディレクトリ名はインストールしたバージョンにより変わる
cd git-2.9.5/


// makeコマンドでインストール
sudo make prefix=/usr/local all

sudo make prefix=/usr/local install


// バージョンを確認
git --version
```
