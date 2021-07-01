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

## /etc/logrotate.d/
- logrotateが読み込むファイルには要件がある
  1. ファイル権限が「444」か「644」であること
  2. ファイル所有者が「root」であること
- コマンドで変更する場合
```sh
sudo chmod 644 {filepath}
sudo chown root:root {filepath}
```

## 設定ファイルの正常性確認
```sh
## -d: --debug
logrotate -dv /etc/logrotate.d/test
# 設定したファイルが読み込まれている出力結果が存在すること

echo $? 
# logrotateコマンドの戻り値が「0」であること
```

# 設定ファイルの正常性確認v2
```sh
# コマンドの戻り値で正常か判断
logrotate -dv /etc/logrotate.conf && [ $? -eq 0 ] && echo "ok"

# デバッグの出力結果から設定したファイルが読み込まれているか確認
logrotate -dv /etc/logrotate.conf 2>&1 | grep {任意のログファイルのパス: /etc/logrotate.d/test}
```

# 活用しやすそうなオプション
## 日付のフォーマットを変更
- デフォルト：{filename.log}-20210701
```sh
filepath {
  deteformat _%Y%m%d
}
```
## 作成されるファイルの権限
```sh
filepath {
  create 755 user user
}
```
