## linuxの文字コードを確認・変更
```
echo $LANG
LANG=ja_JP.UTF8
```

## viで開いたファイルの日本語が文字化けしていた場合
``` 
:set enc?
:set enc=utf-8
```
