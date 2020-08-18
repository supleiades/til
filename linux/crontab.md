# 安全にcrontabを修正する方法

### バックアップ
```
crontab -l > crontab`date '+%Y%m%d'`.org
crontab -l > crontab.edit
```

### 修正と差分確認
意図しない修正がないか確認
```
vi crontab.edit
crontab -l | diff crontab.edit -
```

### 適用と確認
```
crontab crontab.edit
crontab -l
```

## dateコマンドを使用する時の注意点

- % の前に \ を使用する必要がある
```
# ex)
cp /var/log/messages var/log/messages-`date "+\%Y\%m\%d"`

# 参考： https://qiita.com/Kobecow/items/15f07dfe075083ff326d
```
