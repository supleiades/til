## strのTrue/Falseをintの0/1に変換する処理
- 前提条件：
  - boolのTrueはintの1であり、boolのFalseはintの０である
  - 参考： https://python.civic-apps.com/str-to-bool/
```
from distutils.util import strtobool

a = "True"
strtobool(a)
# 1

b = "False"
strtobool(b)
# 0

# 参考： https://qiita.com/koemu/items/fd333fd8ed14f31fbca6
````
