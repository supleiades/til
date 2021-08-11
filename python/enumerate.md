- forの中でリストやタプルのいてらぶるオブジェクトの要素と同時にインデックスを取得する

## インデックスと要素を取得する
```py
l = ["aaa", "ii", "u", "eeeee"]

for i, str in enumerate(l):
    print(i, str)
# 0 aaa
# 1 ii
# 2 u
# 3 eeeee
```

## インデックスを0以外から開始する
- enumerate()の第２引数に開始数値を指定する
```py
l = ["aaa", "ii", "u", "eeeee"]

for i, str in enumerate(l, 10):
    print(i, str)
# 10 aaa
# 11 ii
# 12 u
# 13 eeeee
```


