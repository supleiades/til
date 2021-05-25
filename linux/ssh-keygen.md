# 鍵の作成
`ssh-keygen -t rsa -b 4096`
- 鍵にコメントを入れる
`ssh-keygen -f {ファイル名} -t rsa -b 4096 -C "{コメント}"`

### 秘密鍵から公開鍵を作成する
```
ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

### 鍵の強度を確認する
- 公開鍵のコメントなどの情報を確認する
```
ssh-keygen -lf ~/.ssh/id_rsa.pub
```
- 参照: https://www.atmarkit.co.jp/ait/articles/1908/02/news015.html

## 作成済みの鍵にパスフレーズを付与する
- -m: OpenSSH形式の鍵になってしまうので、それを従来のrsa形式で作成することを指定する
```sh
ssh-keygen -p -N {Passphrase} -m PEM -f {KeyfilePath}
```
- 参考:  https://dev.classmethod.jp/articles/openssh78_potentially_incompatible_changes/https://dev.classmethod.jp/articles/openssh78_potentially_incompatible_changes/
