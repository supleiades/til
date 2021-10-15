# 現在のディレクト以下のファイルを全てzip化
```sh
zip -r {任意のアーカイブ名}.zip .
```

# 現在のディレクトリのファイルをそれぞれzip
- 圧縮しつつ、元のファイルを残す
```sh
find . \! -name "*.zip" -type f -exec zip -j {}.zip {} \;

# 元のファイルを削除する場合
# find . \! -name "*.zip" -type f -exec zip -j {}.zip {} \; -exec rm -f {} \;
```
- 解凍しつつ、zipファイルを削除
```sh
find . -type d -exec unzip {}/*.zip -d {} \;;find . -name "*.zip" -exec rm {} \;
```
- 参考： https://ameblo.jp/pclindesk/entry-10109694180.html 
