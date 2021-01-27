- インスタンスの名前を判定
```py
print(type(MyClass)) # <class 'type'>
c = MyClass() # インスタンス生成
print(type(c)) # <class '__main__.MyClass'>

c = MyClass()
print(isinstance(c, MyClass))   # True
print(isinstance(c, str))       # False
print(isinstance("a", MyClass)) # False
print(isinstance("a", str))     # True

# サブクラスの検証
class A: pass
class B(A): pass
print(issubclass(B, A)) # True
print(issubclass(A, B)) # False
```
# 参考
- https://www.ne.jp/asahi/hishidama/home/tech/python/class.html
