withブロックを使うとブロックの終了時に自動的にクローズされる。
閉じ忘れがなくなるので便利。

```
with open(path) as f:
    print(type(f))
# <class '_io.TextIOWrapper'>
```
