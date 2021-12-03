# initial
`pip install PyYAML`

## ファイルの読み込み
- yaml.safe_load() を使用して読み込む
```py
import yaml

with open('{input_yml_filepath}'} as f:
    obj = yaml.safe_load(f)

print(obj)
...
```

## PythonObject --> YamlObject
```py
import yaml

obj = { 'x': 'XXX', 'y': 100, 'z': [200, 300, 400] }
print(yaml.dump(obj))
```

### --> YamlFile
- 日本語を含む場合
```py
import codecs
import yaml

obj = { 'x': 'あいうえお', 'y': [1, 2, 3] }
with codecs.open('output.yaml', 'w', 'utf-8') as f:
    yaml.dump(obj, f, encoding='utf-8', allow_unicode=True)

## 日本語を含まない場合
### codecsを使わない
### dump時にencoding,allow_unicodeの引数を入れない
# import yaml
#
# obj = { 'x': 'XXX', 'y': 100, 'z': [200, 300, 400] }
# with open('output.yaml', 'w') as file:
#     yaml.dump(obj, file)
```
