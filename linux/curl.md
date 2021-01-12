## -o
```
curl "{url}" -o "{インストール後のファイル名}"
```

# 参考URL
https://qiita.com/ryuichi1208/items/e4e1b27ff7d54a66dcd9


## curlでPOST（discord_Webhook）
```
# curlのオプション
- -H: HTTPヘッダーの指定
- -X: HTTPメソッド指定
- -d: HTTPBodyにパラメータ指定

# discordにWebhooksでテストメッセージを送信するコマンド
- curl -H "Content-Type: application/json" -X POST -d '{"username": "test", "content": "hello"}' {*webhooksURL*}`

# 参考
- https://qiita.com/youtoy/items/c77106a23b60b364b9a0
```
