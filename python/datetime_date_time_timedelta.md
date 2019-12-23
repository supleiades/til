datetimeで生成された値
　datetime.datetime型（datetimeオブジェクト）
　　datetime.now()で取得
　　日付（年、月、日）と時刻（時、分、秒、マイクロ秒）の両方の情報を持つ
  　属性：year, month, day, hour, minute, second, microsecondでアクセス可

　datetime.date型（dateオブジェクト）
 　date.today()で取得可
　　日付（年、月、日）の情報を持つ
  　属性：year, month, dayでアクセス可
   
  datetime.time型（timeオブジェクト）
  　時刻（時、分、秒、マイクロ秒）の情報を持つ
  　属性：hour, minute, second, microsecondでアクセス可
   
  datetime.timedelta型（timedeltaオブジェクト）
  　datetime, dateオブジェクトの引き算でtimedeltaが生成
  　deltatimeオブジェクト同士を引き算でtimedeltaが生成
　
 


# datetimeの値を変数に入れて、各属性を指定してアクセス
datetime(year, month, day, hour=0, minute=0, second=0, microsecond=0, tzinfo=None)
```
dt = datetime.datetime(2018, 2, 1, 12, 15, 30, 2000)
print(dt)
// 2018-02-01 12:15:30.002000

print(dt.minute)
// 15
```

# dateの値を変数に入れて、各属性を指定してアクセス
date(year, month, day)
```
d = datetime.date(2018, 2, 1)
print(d)
// 2018-02-01

print(d.month)
// 2
```

# timeの値を変数に入れて、各属性を指定してアクセス
time(hour=0, minute=0, second=0, microsecond=0, tzinfo=None)
```
t = datetime.time(12, 15, 30, 2000)
print(t)
// 12:15:30.002000

print(t.hour)
// 12
```

# timedeltaのコンストラクタ
timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, minutes=0, hours=0, weeks=0)





