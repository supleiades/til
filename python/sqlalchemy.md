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


## 
```py
from sqlalchemy import func as F
from sqlalchemy import desc
from mo9mo9db.dbtables import Studytimelogs  # noqa: E402, F401
session = Studytimelogs.session()
obj = session.query(Studytimelogs.member_id, F.sum(Studytimelogs.studytime_min)).filter(Studytimelogs.access == "out", Studytimelogs.studytime_min.isnot(None)).group_by(Studytimelogs.member_id).order_by(desc(F.sum(Studytimelogs.studytime_min))).all()

_ = [print(f"[name:{i[0]}] {i[1]}/min ") for i in obj]
> [name:603567991132782592] 1633/min 
> [name:487653156608671744] 779/min 
> [name:405273369718816768] 659/min 
> [name:774508401215799336] 311/min 
> [name:523121850063257600] 86/min 
> [name:756348505261342751] 84/min 
> [name:686227586652962870] 82/min 
> [name:646127851644649474] 75/min 
> [name:730770162739052602] 72/min 
> [name:713005094978846731] 66/min 
> [name:451763787821744137] 63/min 
> [name:689449857672282158] 62/min 
> [name:389642122376118273] 45/min 
> [name:777862430063591424] 38/min 
> [name:798147954841485333] 33/min 
> [name:371142888412938252] 28/min 
> [name:186844273029677056] 18/min 
> [name:801336569944473610] 18/min 
> [name:698350641638277180] 15/min 
> [name:669117688530075648] 9/min 
> [name:402281699414900737] 5/min 
> [name:414804663410360331] 5/min 
> [name:825252908986925056] 0/min
```

## テーブルの作成・削除
```py
# Selfintroduction: sqlalchemyの書式に従い、任意で指定したテーブルのオブジェクト
# engine: sqlalchemy.create_engineから作成されるオブジェクト

Selfintroduction.__table__.drop(engine)
Selfintroduction.__table__.create(engine)
```

## テーブル作成時に指定できる情報
```py
class Selfintroduction(DBBaseMixin, Base):
    __table_args__ = ({"mysql_charset": "utf8mb4",
                       "mysql_row_format": "DYNAMIC",
                       "mysql_collate": "utf8mb4_bin"})
    id = Column(Integer, autoincrement=True)
    ...
```

## テーブル一括削除・作成
```py
from sqlalchemy.ext.declarative import declarative_base

from mo9mo9db.dbsession import get_db_engine

Base = declarative_base()
engine = get_db_engine()

Base.metadata.drop_all(bind=engine)
Base.metadata.create_all(bind=engine)
```

# メモ
```py
>>> get_db_session().bind.table_names()
...
021-02-23 13:22:39,769 INFO sqlalchemy.engine.base.Engine SHOW FULL TABLES FROM `VCtimeRecord`
2021-02-23 13:22:39,769 INFO sqlalchemy.engine.base.Engine {}
['studymembers', 'studytags', 'studytimelogs']
```
