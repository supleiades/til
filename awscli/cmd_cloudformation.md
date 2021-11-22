コマンドラインからCloudFormationを使ってみよう

# 作成
```
aws cloudformation deploy --template-file {file_name} --stack-name {create stack_name}
```

# 削除
```
aws cloudformation delete-stack --template-file {file_name} --stack-name {delete stack_name}
```
