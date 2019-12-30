# 日付を指定フォーマットで取得

```
from datetime import datetime

today = datetime.today()
strtoday = datetime.strftime(today, '%m/%d')
print(strtoday)

# 今日が2019年12月30日ならstrtodaは「12/30」になる

```
