# 大文字から小文字に名前を変更
## ファイル名の変更
- -fオプションを付与して強制的に名前変更を行う
```
git mv FILENAME filename
```

## ディレクトリ名の変更
- unix環境だと大文字小文字の区別がないため、別名に置き換えてから名前を変更する
```
git mv DIRENAME/ _dirname/
git mv _dirname/ dirname/
```
