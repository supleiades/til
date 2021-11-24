データをインポートできれば、sqlのように必要な情報のみを取得できる

- インポート
```py
import pandas as pd
```

### 必要な情報を取得
- [参考ページ](https://note.nkmk.me/python-pandas-str-contains-match/)
```py
# pd_j: pandasのパッケージでデータをインポート済みのオブジェクト
pd_j[pd_j["id"] == 603567991132782592]

```

### jsonデータをpandasに読み込む
- [参考ページ](https://note.nkmk.me/python-pandas-json-normalize/)
```py
import pandas as pd

l_nested = [{'name': 'Alice', 'age': 25, 'id': {'x': 2, 'y': 8}},
            {'name': 'Bob', 'id': {'x': 10, 'y': 4}}]


pd.DataFrame(l_nested)
#     name   age                 id
# 0  Alice  25.0   {'x': 2, 'y': 8}
# 1    Bob   NaN  {'x': 10, 'y': 4}

pd.json_normalize(l_nested)
#     name   age  id.x  id.y
# 0  Alice  25.0     2     8
# 1    Bob   NaN    10     4
```
