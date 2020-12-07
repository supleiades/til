## json形式の文字列をjsonのシンタックスでみやすく表示
```
import json

str_json = {json形式の文字列}

json.dumps(str_json, indent=2)
# {
#   ###json形式の文字列がいい感じに表示される###
# }
```
