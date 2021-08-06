# ステータス確認
```
systemctl status <service名> -l
## ログの詳細をみるには「-l」のオプションを付与する

## リアルタイムにログを表示して確認したい場合
journalctl -f -u <service名>
```

## サービス確認
```
systemctl list-unit-files --type=service
```

## 自動起動
- 自動起動確認
```
systemctl is-enabled
```
- 自動起動on
```
systemctl enable
```
- 自動起動off
```
systemctl disable
```
