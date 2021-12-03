辞書をループ処理させるためのメソッド「keys()」「valuew()」「items()」

## keys()
```py
d = {'key1': 1, 'key2': 2, 'key3': 3}
for k in d.keys():
    print(k)
# key1
# key2
# key3
```

## values()
```py
d = {'key1': 1, 'key2': 2, 'key3': 3}
for v in d.values():
    print(v)
# 1
# 2
# 3
```
### values() + list形式
```py
values = d.values()
# dict_values([1, 2, 3]) # type(v): <class 'dict_values'>

v_list = list(d.values())
# [1, 2, 3] # <class 'list'>

```

## items()
```py
d = {'key1': 1, 'key2': 2, 'key3': 3}

for k, v in d.items():
    print(k, v)
# key1 1
# key2 2
# key3 3
```
### items() + タプル形式
```py
d = {'key1': 1, 'key2': 2, 'key3': 3}

for t in d.items():
    print(t)
    print(type(t))
    print(t[0])
    print(t[1])
    print('---')
# ('key1', 1)
# <class 'tuple'>
# key1
# 1
...
```

## dictitems = d.items()
```py
d = {'key1': 1, 'key2': 2, 'key3': 3}

items = d.items()
print(items)
print(type(items))
# dict_items([('key1', 1), ('key2', 2), ('key3', 3)])
# <class 'dict_items'>

i_list = list(d.items())
print(i_list)
print(type(i_list))
# [('key1', 1), ('key2', 2), ('key3', 3)]
# <class 'list'>

print(i_list[0])
print(type(i_list[0]))
# ('key1', 1)
# <class 'tuple'>
```
