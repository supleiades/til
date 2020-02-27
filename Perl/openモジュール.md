## ファイル入出力

#### 読み込み
```
open(my $in "<", "filename.txt") or die("Error");
while (<$in>) {
  print $_;
}
close($in);
```


#### 書き込み
ファイルから読み込んだ値を別のファイルに書き込むフロー（標準出力には何も表示されない）
```
open(my $in "<", "filename.txt") or die("Error");
open(my $out ">", "outfilename.txt") or die("Error");
while (<$in>) {
  print $out $_; # inから取得した値を標準出力の代わりにoutのファイルに書き込む
}
close($in);
close($out);
```
