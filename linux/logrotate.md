# logrotateとは
- PATH： /etc/logrotate.d/
- ログを決められた期間でまとめて別ファイルに置き換えて保存してくれる
- 一定期間経ったローテーションしたファイルを削除してくれる
- その際、ローテーションしたファイルは設定によって圧縮できたりもする
- これはデーモンとして実行されてはいない
  - cronから呼び出されている
    - /etc/cron.daily
  - 参考（１）：https://www.rep1.co.jp/staff/200vcxg/217rav/logrotate_lcd_-linux_command_d.htm
  - 参考（２）：https://www.rep1.co.jp/staff/200vcxg/217rav/logrotate_lcd_-linux_command_d_1.htm


## /etc/logrotate.conf
- /etc/logrotate.d/配下がこのファイルからincludeされて読み込まれる
  - デフォルト設定をlogrotate.dに配置したファイルで上書きしたものが実行される
  - logrotate.dを以下のようにすると、デフォルト（/etc/logrotate.conf）の設定が適応される
```
# cat /etc/logrotate.d/test 
/var/log/test.log {
}
```
- 参考サイト：https://qiita.com/Esfahan/items/a8058f1eb593170855a1

## 設定ファイルの正常性確認
``` 
## -d: --debug
logrotate -dv /etc/logrotate.d/test
# 設定したファイルが読み込まれている出力結果が存在すること

echo $? 
# logrotateコマンドの戻り値が「0」であること
```


