## 既存ファイルに退避
- masterブランチのファイル達は後に必要になるので一旦別のブランチに退避させてmasterをリセットさせる方法
```
# 現在のmasterブランチを退避
git branch -b {退避先のブランチ名}

# 元masterブランチをリモートの別ブランチとして保存
git push origin {退避先のブランチ名}

# masterブランチに戻って
git checkout master

# マスターを元にログを引き継がないでブランチを作成
git checkout --orphan {仮のブランチ名}

# masterブランチにいないことを一応確認してから、全てのファイルを削除
git branch 
git rm -rf .
（必要であれば：rm -rf *）

# 空になったこのブランチを元にmasterブランチを作成
git checkout --orphan master
git checkout -b master

# 空のmasterをリモートに保存するためにからコミット＋プッシュ
git commit --allow-empty -m "{masterを初期化したことに関するメモ}"
git push origin master
```

## 旧リポジトリをmaster以外のリポジトリに一時保存してからmasterにマージする
```
# 別リポジトリからpullするための準備
git remote add {任意のoriginに代るリモートアクセス先別名} {旧リポジトリのcloneURL}
git checkout -b {旧環境をcloneする任意のブランチ名}

# 旧リポジトリのファイル群をpullする。ちなみに私は今回旧リポジトリのmasterブランチを取得したいのでmasterを指定
# ログも全て取得したいので、オプション付与
git pull {任意のoriginに代るリモートアクセス先別名} master --allow-unrelated-histories

# push
git push origin {旧環境をcloneする任意のブランチ名}

# ブラウザからmasterにマージする
