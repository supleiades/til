## リポジトリでauthor情報を追加してない際の変更方法

- author情報をリポジトリ内に追加
```sh
git config --local user.name {ユーザー名}
git config --local user.email {メールアドレス}

```

- 現在のauthor情報に更新(vi環境に移動)
```sh
git commit --amend --reset-author
```
