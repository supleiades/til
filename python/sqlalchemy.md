# 準備
- どのDBのデータを操作するかなどをクラスに定義することで初めて使用できる様になる
```py
from sqlalchemy import create.engine
from sqlalchemy.orm import scoped_session, sessionmaker
from sqlalchemy.ext.declarative import declarative_base

# ------------------------
# 独自のデータベースの情報を外部ファイルに格納している物を読み込む
import config as cfg
# ------------------------

engine = create_engine(
    f"mysql+pymysql://{cfg.DB_user}:{cfg.DB_password}@{cfg.DB_host}:{cfg.DB_port}/{cfg.DB_database}", 
    convert_unicode=True, 
    echo=True
)

session = scoped_session(
    sessionmaker(
        autocommit = False,
        autoflush = False,
        bind = engine
    )
)

Base = declarative_base()
Base.query = session.query_property()

```

## INSERT
- 書き込み
```py
insertrecord = ClassTable(No=1, Name="SuPleiades", sex="man")
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
`
- 20つ取得
```py
session.query({操作したいテーブルのクラス}).filter({操作したいテーブルのクラス}.{カラム名} == {取得したい値}).limit(20).all()
```

## UPDATE
- 変更したいレコードを１つ指定して変更
```py
updaterecord = session.query({操作したいテーブルのクラス}).filter({操作したいテーブルのクラス}.{カラム名} == {取得したい値}).first()
updaterecord.sex = woman
updaterecord.commit()
```

## DELETE
```py
deleterecord = session.query({操作したいテーブルのクラス}).filter({操作したいテーブルのクラス}.{カラム名} == {取得したい値}).delete()

```
