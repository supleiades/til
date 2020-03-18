# シェルスクリプトの小技
シェルスクリプトを書く際に役立つコマンドや書式

xargs 

前のコマンドの結果を1行ずつ次のコマンドに渡す
```
ls | xargs wc -l 
```


uniq

重複データに関する処理

英語的には「重複していないデータ」という意味


sort

並び替え



seq

指定した数字までを繰り返し表示する
```
seq 3
# 1
# 2
# 3
seq -w 10
# 01
# 02
# 03
# 04
# 05
# 06
# 07
# 08
# 09
# 10
seq 2 4
# 2
# 3
# 4
seq 1 2 5
# 1
# 3
# 5
seq 3 | tac
# 3
# 2
# 1
seq -f "IMG%03g.jpg" 3
# IMG001.jpg
# IMG002.jpg
# IMG003.jpg
// %g：整数で出力する際の桁数を指定(ex:4桁の幅であれば「%4g」、4桁で「0001」のようにゼロで埋めるならば「%04g」)
// %e：指数形式（大文字で出力するときは「%E」）
// %f：小数点形式
```

# 実行場所を意識せずスクリプトを実行したい場合
```
#!/bin/sh
cd `dirname $0`
pwd
```

## dirname
```
$ dirname /home/vagrant/sample.sh 
/home/vagrant
```

## $0
```
$ basename /home/vagrant/sample.sh 
sample.sh
```
