- ファイル内の文字列が含まれたフォルダを検索
```
find [検索対象フォルダのパス] -type f -print | xargs grep '[検索したい文字列]'
```

- 変更（Modify)の時間が直近10分以内のもの数量を表示
```
find {フォルダのパス} -type f -cmin -10 | wc -l
```

- カレントディレクトリ配下のディレクトリ内の最新更新日のファイルを表示
```
for d in `find ./ -maxdepth 1 -type d`; do echo $d `find $d -type f -print | xargs -i ls -l --time-style=long-iso "{}" | sort -k 6,7 | tail -1`;done
```

## xargs
### -I(アイ：オプション）
```
grep -l bash /etc/* 2>/dev/null | xargs -I {} echo "[" {} "]"

（{}の位置にファイル名が入る）
```
