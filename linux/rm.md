# ファイル 名に特種文字を使っているファイルを削除する方法

```
$ ls -li
12768597 -rw-r--r-- 1 ec2-user ec2-user  312 12月 25 07:07 -

$ find . -inum 12768597
./-la

$ rm `find . -inum 12768597`

$ find . -inum 12768597
```
