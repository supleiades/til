- 「f文字列」も以下の形で使用可能
```py
import re

str = [達成度]83%|████████████▌----|\n--->現在の積み上げ：25h\n--->週の目標時間　：10h
weekstudyhtime = 25
targettime = 10

re.sub(rf"{str(weekstudyhtime)}h$", f"{str(targettime)}h", str)
```
