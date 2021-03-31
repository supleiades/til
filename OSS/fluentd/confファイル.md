# gcpのfluentdのデフォルト配置場所
- /etc/google-fluentd/config.d

# conf
## ログをそのままloggingに送る
- 設定を追加した場合再起動する
  - すると、posファイルが作られる
```
<source>
  @type tail
  format none
  path {ログのファイル名}
  pos_file /var/lib/google-fluentd/pos/{任意なファイル名}
  read_from_head true
  tag {任意なタグ名}
</source>
```
