- 特定のロールの情報を確認
```
gcloud iam roles describe {role name} --project $DEVSHELL_PROJECT_ID
```

- プロジェクト内のカスタムロールの権限一覧を確認
```
gcloud iam roles list --project $DEVSHELL_PROJECT_ID
```

- ロールを新規作成
```
gcloud iam roles create {role name} --project $DEVSHELL_PROJECT_ID --file role.yaml
```

- ロールの権限を更新
```
gcloud iam roles update {role name} --project $DEVSHELL_PROJECT_ID --file update-role.yaml
```

- ロールの無効化
```
gcloud iam roles update {role name} --project $DEVSHELL_PROJECT_ID --stage DISABLED
```

- ロールの削除
```
gcloud iam roles delete {role name} --project $DEVSHELL_PROJECT_ID
```
