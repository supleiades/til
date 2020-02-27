## 区切り文字は「;（セミコロン）」
```
for (my $i = 0; i < 10; $i++){
}
```

#### 「foreach」と「for」は同じ
```
foreach ( ){
}

#for (){
#}
```

## 配列の値を取りだしてループ処理
#### 基本
```
my @list = qw(red green blue);
foreach $str (@list) {
  print "color = $str\n";
```

#### 省略形（基本系と同様の処理）
配列を取り出した時の変数を「$_ 」と省略できる
```
my @list = qw(red green blue);
for (@list) {
  print "color = $_\n";
```



## ハッシュの値を取りだしてループ処理
my

