
- AttributeError: 'DMChannel' object has no attribute 'category_id'
- このエラーの時にif文に処理を流す方法（属性があるかどうかの判定処理）
```
        if not hasattr(message.channel, "category_id"): 
            return
```
