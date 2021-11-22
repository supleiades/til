コマンドラインからCloudFormationを使ってみよう

- 作成
```
aws cloudformation deploy --template-file {file_name} --stack-name {create stack_name}
```

- 削除
```
aws cloudformation delete-stack --template-file {file_name} --stack-name {delete stack_name}
```

- コマンドラインからパラメーターの値を指定
```
aws cloudformation deploy --template-file {file_name} --stack-name {create stack_name} --parameter-overwrite {parameter_key}={parameter_value}
```

- コマンドラインからパラメータのファイルを指定してパラメーターの値を指定
```
aws cloudformation deploy --template-file {file_name} --stack-name {create stack_name} --parameter-overwrite $(cat {parameter_filename})

```

- スタックの情報を取得
```
aws cloudformation describe-stack-resource --stack-name {create stack_name} --logical-resource-id {Resource_name}
```
