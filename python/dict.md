## 辞書型の作成
- 1
```py
dict1 = {"key1": "value1", "key2": "value2"}
```
- 2
```py
dict1 = dict(key1=value1, key2=value2)
```
- 3
```py
dict1 = dict([("key1", "value1"), ("key2", "value2"), ("key3", "value3")])
```
- 4
```py
list1 = ["key1", "key2"]
list2 = ["value1", "value2"]

dict1 = dict(zip(list1, list2)

```

## 辞書の連結
```py
dist1 = {"key1": "value1", "key2": "value2"}
dict2 = {"key3": "value3", "key4": "value4"}

# v3.5から使用可能なやり方
dict3 = {**dict1, **dict2, "value5": "value5"}
```

## 辞書から要素削除
```py
dict1.pop("key1")
```

