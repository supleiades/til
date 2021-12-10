## rm -rfで削除できない名前のファイルを削除する方法
```sh
# 対象のinodeを調べる
ls -i 

# 削除する
## -p： 実行前に確認を行う
find . -inum {inode番号} | xargs -p rm -rf
```
