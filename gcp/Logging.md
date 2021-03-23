## 各ファイルを説明
### /var/lib/google-fluentd/pos/
- どこまでログを送ったかの記録ファイル
### /etc/google-fluentd/config.d/
- fluentのconfファイル
- どこのファイルをどの様な設定でGCP-loggingに送るかの設定

## posファイルについて
- このファイルはサービス起動時に作成される
- ファイルの中身「ログファイル名　読み込んだファイルのバイト数　ログファイルのinode」
### fluentdが起動している時にposファイルを削除してしまった場合
```
systemctl stop google-fluentd
systemctl start google-fluentd
```
