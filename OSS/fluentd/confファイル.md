# gcpのfluentdのデフォルト配置場所
- /etc/google-fluentd/config.d

# conf
## ログをそのままloggingに送る
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
