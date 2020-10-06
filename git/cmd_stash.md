### 変更を退避する（名前をつけて）
```
git stash save "{message}"
```

### 退避した作業を戻す
```
git stash apply stash@{0}
```

### 退避した作業の一覧を表示
```
git stash list
```

### 作業の詳細を確認
```
git stash show stash@{0}
```

### add以外を退避する
```
git stash -k
```

### 退避した作業を全て消す
```
git stash clear
```

### 退避した作業を指定して消す
```
git stash drop stash@{0}
```
