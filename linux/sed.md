# 複数のファイルの特定文字を一括置換したい

## オプション
- 「\1」は1つ目「()」部分
- 「\2」は2つ目の「()」部分に対応します
- 「&」は対象となった行全体を参照
- 「()」は拡張正規表現なので、「\(」「\)」のように「\」を付ける
  - or「-r」オプション付きで実行する必要
- 「-n」オプション＆「s」コマンドの「p」オプションで置換処理を行った行だけを出力

### ファイルの確認
```
$ ls -1
aaa
udem-image2.jpg
udem-image3.jpg
udem-image4.png
udem-image.jpg
```

### マッチした対象の置換後の文字列を出力・実行
```
$ ls -1 | sed -nr "s/^udem(.*)/sudo mv & udemy-\1/p" 
sudo mv udem-image2.jpg udemy--image2.jpg
sudo mv udem-image3.jpg udemy--image3.jpg
sudo mv udem-image4.png udemy--image4.png
sudo mv udem-image.jpg udemy--image.jpg
$ ls -1 | sed -nr "s/^udem(.*)/sudo mv & udemy-\1/p" |bash
```

### 一部置換しなおしたい場合（「udemy--image」を「udemy-image」に変更したい）
```
$ ls -1 | sed -nr "s/(^udemy-)-(.*)/sudo mv & \1\2/p"
sudo mv udemy--image2.jpg udemy-image2.jpg
sudo mv udemy--image3.jpg udemy-image3.jpg
sudo mv udemy--image4.png udemy-image4.png
sudo mv udemy--image.jpg udemy-image.jpg
$ ls -1 | sed -nr "s/(^udemy-)-(.*)/sudo mv & \1\2/p"|bash
```

# 完成！
```
$ ls -1
aaa
udemy-image2.jpg
udemy-image3.jpg
udemy-image4.png
udemy-image.jpg
```

参考URL： https://www.atmarkit.co.jp/ait/articles/1610/18/news008.html
