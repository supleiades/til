# logrotateとは
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
/etc/logrotate.d/test {
}
```


参考サイト：
https://qiita.com/Esfahan/items/a8058f1eb593170855a1

PATH： /etc/logrotate.d/

