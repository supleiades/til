# 一時的な対応
## getenforce
- 現在の設定確認
```sh
getenforce
```
- 無効化
```sh
setenforce 0

getenforce
# Permissive
```
- 有効化
```sh
setenforce 1

getenforce
# Enforcing
```

# 永久的な対応
## /etc/selinux/config
- 設定ファイルの書き換え
  - 再起動必要（reboot）
```sh
$ sudo vi /etc/selinux/config
SELINUX=enforcing

```
