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

### resetした場合は強制pushが必要
- ブランチ名の前に「+」を付ける
  - 基本的にリモートのコミットを無かったことにするので強制権限でpushする必要がある
  - 普段のpushコマンドにとある文字を加えて実行する
```sh
git push {remote名} +{branch名}
```
or
```sh
git push -f {remote名} {branch名}

```

### リモートのコミットログだけを戻す
- ローカルのファイルはそのまま
- リモートのブランチのみ決めうちで戻す
```sh
git push -f origin {コミットID}:{ブランチ名}
```
# resetを取り消したい
```
git reset --abort
```
