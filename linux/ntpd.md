- 設定ファイル
/etc/ntp.conf

- 設定値確認
```
ntpq -p
```

# 設定の反映
- 設定ファイル変更後は再起動する必要がある
```
/etc/init.d/ntpd restart
```
