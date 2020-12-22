## ブランチ同士の差分
```
git diff {ブランチ名} {ブランチ名}
```

## ブランチとリモート
```
# git diff {ローカルブランチ} {リモートブランチ} -- {ファイル名} 
git diff master origin/master -- rolesmaneger.js
```

## ..や...の違い
```
git diff foo..barはgit diff foo barと同じ

## ..
- git rev-list foo..barは、ブランチbarにあってブランチfooにないものすべてを表示します。

## ...
- 一方で、git rev-list foo...barは、fooとbar両方に存在するコミットすべてを表示します
```
