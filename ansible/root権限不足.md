# エラー文
```
fatal: [localhost]: FAILED! => {"changed": false, "changes": {"installed": ["httpd"]},
  "msg": "You need to be root to perform this command.\n",
  "rc": 1, 
  "results": ["Loaded plugins: fastestmirror\n"]
}
```

# 対策
- root権限が不足していた
```
rootで実行するには、becomeを指定する(デフォルトはfalse)。
becomeをtrueにすると、デフォルトでroot実行となる。
becomeでroot権限で実行するには、そのホスト上でsudo su -がパスワードなしでrootでシェル起動できる設定になっている必要がある。
```

### 参考
https://qiita.com/zaki-lknr/items/3ac4c7e105609a7f0bf9#yum%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%A8root%E6%A8%A9%E9%99%90
