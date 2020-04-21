```
/*git コマンドで最新リポジトリをクローン*/
git clone git://git.kernel.org/pub/scm/git/git.git

/*pullして、最新のソースを取得して再度コンパイル*/
cd git
git pull
make all && sudo make prefix=/usr/local install // 見ての通り、コマンド短縮形

/*最終確認*/
git --version
```
