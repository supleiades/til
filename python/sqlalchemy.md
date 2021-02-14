## INSERT
- 書き込み
```py
inserttable = ClassTable(No=1, Name="SuPleiades", sex="man")
session.add(inserttable)
session.commit()
```

## SELECT
- 取得した値にヒットする結果を全て取得
```py
session.query({操作したいテーブルのクラス}).filter({操作したいテーブルのクラス}.{カラム名} == {取得したい値}).all()
```
- 1つのみ取得
```py
session.query({操作したいテーブルのクラス}).filter({操作したいテーブルのクラス}.{カラム名} == {取得したい値}).first()
```
- 20つ取得
```py
session.query({操作したいテーブルのクラス}).filter({操作したいテーブルのクラス}.{カラム名} == {取得したい値}).limit(20).all()
```

## 
