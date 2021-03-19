- 全て１行表示だが、オブジェクト全表示
```
import inspect

inspect.getmembers({確認したいオブジェクト名})
```


### クラスの中身を確認する方法
```py
from pprint import pprint
import inspect

book1 = Studymembers.session().query(Studymembers).all()
print(type(book1))
for i in book1:
    print(type(i))
    pprint(inspect.getmembers(i), indent=4)
#<class 'dbtables.Studymembers'>
#[   ('__class__', <class 'dbtables.Studymembers'>),
#    (   '__delattr__',
#        <method-wrapper '__delattr__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__dict__',
#        {   '_sa_instance_state': <sqlalchemy.orm.state.InstanceState object at 0x7f64634bb370>,
#            'created_at': None,
#            'enrollment': None,
#            'guild_id': '470074961617354773',
#            'id': 1,
#            'joined_dt': datetime.datetime(2021, 1, 15, 9, 5, 1),
#            'member_id': '603567991132782592',
#            'member_name': 'SuPleiades',
#            'organize': None,
#            'selfintroduction_id': None,
#            'times_id': None,
#            'update_dt': None,
#            'updated_at': None}),
#    (   '__dir__',
#        <built-in method __dir__ of Studymembers object at 0x7f64634bb3a0>),
#    ('__doc__', None),
#    (   '__eq__',
#        <method-wrapper '__eq__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__format__',
#        <built-in method __format__ of Studymembers object at 0x7f64634bb3a0>),
#    (   '__ge__',
#        <method-wrapper '__ge__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__getattribute__',
#        <method-wrapper '__getattribute__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__gt__',
#        <method-wrapper '__gt__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__hash__',
#        <method-wrapper '__hash__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__init__',
#        <bound method __init__ of <dbtables.Studymembers object at 0x7f64634bb3a0>>),
#    (   '__init_subclass__',
#        <built-in method __init_subclass__ of DeclarativeMeta object at 0xf3e510>),
#    (   '__le__',
#        <method-wrapper '__le__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__lt__',
#        <method-wrapper '__lt__' of Studymembers object at 0x7f64634bb3a0>),
#    ('__mapper__', <Mapper at 0x7f6463a548b0; Studymembers>),
#    ('__module__', 'dbtables'),
#    (   '__ne__',
#        <method-wrapper '__ne__' of Studymembers object at 0x7f64634bb3a0>),
#    ('__new__', <built-in method __new__ of type object at 0x921120>),
#    (   '__reduce__',
#        <built-in method __reduce__ of Studymembers object at 0x7f64634bb3a0>),
#    (   '__reduce_ex__',
#        <built-in method __reduce_ex__ of Studymembers object at 0x7f64634bb3a0>),
#    (   '__repr__',
#        <bound method DBBaseMixin.__repr__ of <dbtables.Studymembers object at 0x7f64634bb3a0>>),
#    (   '__setattr__',
#        <method-wrapper '__setattr__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__sizeof__',
#        <built-in method __sizeof__ of Studymembers object at 0x7f64634bb3a0>),
#    (   '__str__',
#        <method-wrapper '__str__' of Studymembers object at 0x7f64634bb3a0>),
#    (   '__subclasshook__',
#        <built-in method __subclasshook__ of DeclarativeMeta object at 0xf3e510>),
#    (   '__table__',
#        Table('studymembers', MetaData(bind=None), Column('id', Integer(), table=<studymembers>, primary_key=True, nullable=False), Column('update_dt', DateTime(timezone=True), table=<studymembers>, onupdate=ColumnDefault(datetime.datetime(2021, 2, 23, 17, 25, 22, 341835))), Column('guild_id', String(length=20), table=<studymembers>), Column('member_id', String(length=20), table=<studymembers>, primary_key=True, nullable=False), Column('member_name', String(length=40), table=<studymembers>), Column('selfintroduction_id', String(length=20), table=<studymembers>), Column('times_id', String(length=20), table=<studymembers>), Column('joined_dt', DateTime(), table=<studymembers>), Column('organize', Boolean(), table=<studymembers>), Column('enrollment', Boolean(), table=<studymembers>), Column('created_at', DateTime(), table=<studymembers>, default=ColumnDefault(<function datetime.now at 0x7f6463a6e280>)), Column('updated_at', DateTime(), table=<studymembers>, default=ColumnDefault(<function datetime.now at 0x7f6463a6e310>)), schema=None)),
#    ('__tablename__', 'studymembers'),
#    (   '__weakref__',
#        <weakref at 0x7f64634b5a40; to 'Studymembers' at 0x7f64634bb3a0>),
#    ('_decl_class_registry', <WeakValueDictionary at 0x7f6463caf550>),
#    (   '_sa_class_manager',
#        <ClassManager of <class 'dbtables.Studymembers'> at 7f64634e0c70>),
#    (   '_sa_instance_state',
#        <sqlalchemy.orm.state.InstanceState object at 0x7f64634bb370>),
#    (   'all_get',
#        <bound method DBBaseMixin.all_get of <class 'dbtables.Studymembers'>>),
#    ('created_at', None),
#    (   'delete',
#        <bound method DBBaseMixin.delete of <dbtables.Studymembers object at 0x7f64634bb3a0>>),
#    ('enrollment', None),
#    ('guild_id', '470074961617354773'),
#    ('id', 1),
#    (   'insert',
#        <bound method DBBaseMixin.insert of <class 'dbtables.Studymembers'>>),
#    ('joined_dt', datetime.datetime(2021, 1, 15, 9, 5, 1)),
#    ('member_id', '603567991132782592'),
#    ('member_name', 'SuPleiades'),
#    ('metadata', MetaData(bind=None)),
#    (   'objects',
#        <bound method DBBaseMixin.objects of <class 'dbtables.Studymembers'>>),
#    ('organize', None),
#    (   'save',
#        <bound method DBBaseMixin.save of <dbtables.Studymembers object at 0x7f64634bb3a0>>),
#    ('selfintroduction_id', None),
#    (   'session',
#        <bound method DBBaseMixin.session of <class 'dbtables.Studymembers'>>),
#    ('times_id', None),
#    ('update_dt', None),
#    ('updated_at', None)]
```