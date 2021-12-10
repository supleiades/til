指定したコミット時点にコミット情報を戻す

## コミットのみを戻し、ファイルは残す場合
- --soft
```sh
git reset --soft {commitID}
```

## コミットと共にファイルもその時点に戻す
- --hard
```sh
git reset --hard {commitID}
```
