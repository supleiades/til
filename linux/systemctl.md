# ステータス確認
```
systemctl status <service名> -l
## ログの詳細をみるには「-l」のオプションを付与する

## リアルタイムにログを表示して確認したい場合
journalctl -f -u <service名>
```
