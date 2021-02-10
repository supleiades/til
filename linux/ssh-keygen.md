# 鍵の作成
`ssh-keygen -t rsa -b 4096`
- 鍵にコメントを入れる
`ssh-keygen -t rsa -b 4096 -C "{コメント}"`
  - 既存の鍵にコメントを入れる
  - https://www.it-swarm.jp.net/ja/ssh/%E6%97%A2%E5%AD%98%E3%81%AEssh%E5%85%AC%E9%96%8B%E9%8D%B5%E3%81%AB%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88%E3%82%92%E8%BF%BD%E5%8A%A0%E3%81%99%E3%82%8B/960125689/
- 公開鍵のコメントなどの情報を確認する
`ssh-keygen -lf {公開鍵のパス}`

# 秘密鍵から公開鍵を作成する
```
ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

# 鍵の強度を確認する
```
ssh-keygen -l -f ~/.ssh/id_rsa.pub
```


## 参照
- https://www.atmarkit.co.jp/ait/articles/1908/02/news015.html
