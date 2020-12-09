### ブランチの作成と作成ブランチに移動
```
git checkout -b {ブランチ名}
```

### リモートブランチをローカルに持ってくる方法
```
git remote -v
# 出力結果に取得したいブランチがある前提

git checkout -b {branch名} {origin/{branch名}}
```
