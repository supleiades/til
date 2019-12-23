 # datetimeモジュールで利用できるオブジェクト
 datetime.datetime：日付と時間
 
 datetime.date：日付
 
 datetime.time：時間
 
 datetime.timedelta：時間差・経過時間
 

# 変換方法
　.strftime()
 
  .strptime()
  
  
# datetime型 --> 文字列に変換
.strftime({形式コード})
```
# 2018-02-02 18:31:13

print(d_today.strftime('%y%m%d'))
# 180202

print(d_today.strftime('%A, %B %d, %Y'))
# Friday, February 02, 2018

print(d_today.strftime('%Y年%m月%d日'))
# 2018年02月02日

print('日番号（1年の何日目か / 正月が001）:', d_today.strftime('%j'))
print('週番号（週の始まりは日曜日 / 正月が00）:', d_today.strftime('%U'))
print('週番号（週の始まりは月曜日 / 正月が00）:', d_today.strftime('%W'))
# 日番号（1年の何日目か / 正月が001）: 033
# 週番号（週の始まりは日曜日 / 正月が00）: 04
# 週番号（週の始まりは月曜日 / 正月が00）: 05
```

# 文字列 --> datetime型
.strptime({str}, {形式コード})
```
date_str = '2018/2/1 12:30'
date_dt = datetime.datetime.strptime(date_str, '%Y/%m/%d %H:%M')
print(date_dt)
# 2018-02-01 12:30:00

print(type(date_dt))
# <class 'datetime.datetime'>
```

# datetimeでフォーマット
```
date_str = '2018/2/1 12:30'
date_dt = datetime.datetime.strptime(date_str, '%Y/%m/%d %H:%M')
print(date_dt.strftime('%Y年%m月%d日 %H時%M分'))
# 2018年02月01日 12時30分
```

# datetime型でtimedelta使って数日前の日付取得
```
date_str = '2018年2月1日'
date_format = '%Y年%m月%d日'
td_10_d = datetime.timedelta(days=10)

date_dt = datetime.datetime.strptime(date_str, date_format)
date_dt_new = date_dt - td_10_d
date_str_new = date_dt_new.strftime(date_format)

print(date_str_new)
# 2018年01月22日

```



.nowではなく、.utcnow()を使う場合マイクロ秒も表記される
　文字列からdatetime型に戻す場合の秒とマイクロ秒の表記 --> "%S.%f"


# 形式コード
- 曜日
%a　：ロケールの曜日名の短縮形 (Sum,Mon,...,Sat(en_US))
$A　：ロケールの曜日名 (Sunday,Monday,...,Saturday(en_US))
%w　：10進数で表記した曜日で0が日曜日、6が土曜日 (0,1,...,6)
- 日
%d　：0埋めした10進数の月中の日にち (1,2,...,31)
%j　：0埋めした10進数の年中の日にち (001,002,...,336)
- 週
%U　：新年初「日曜日」を0週に属する、0埋めした10進数の年中の週番号 (00,01...,53)
%W　：新年初「月曜日」を0週に属する、0埋めした10進数の年中の週番号 (00,01...,53)
- 月
%b　：ロケールの月名の短縮形 (Jan,Deb,...,Dec(en_US))
%B　：ロケールの月名 (January,February,...,December(en_US))
%m　：0埋めした10進数の月 (01,02,...,12)
- 年
%y　：0埋めした10進数の世紀なしの年 (00,01,...,99)
%Y　：4桁の西暦 (0001,0002,...,9999)
- 時
%H　：0埋めした10進数の24時間 (00,01,...,23)
%I　：0埋めした10進数の12時間 (00,01,...,12)
%p　：ロケールのAMかPMの文字列 (AM,PM(en_US)
- 分
%M　：0埋めした10進数の分 (00,01,...,59)
- 秒
%S　：0埋めした10進数の秒 (00,01,...,59)
- マイクロ秒
%f　：左から0埋めした10進数のマイクロ秒 (000000,000001,...,999999)
- タイムゾーン
%Z　：タイムゾーンの名前、オブジェクトがnaiveであれば空文字 ({空文字列},UTC,EST,CST)
- ロケール
%c　：適切な形式で表したロケールの日時 (Tue Aug 16 21:30:00 1988 (en_US))
%x　：適切な形式で表したロケールの日付 (08/16/88 (None),08/16/1988 (en_US))
%X　：適切な形式で表したロケールの時間 (21:30:00 (en_US))
- その他
%%　：文字'%'を表す
  
