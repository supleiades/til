# バケットとSCLについて
- バケットのaclを操作するには、GUIでバケット作成時に「きめ細やかな権限設定」をする必要がある
- CLIからバケットを作成する時は、これがデフォルトで設定される？？（わからん

### オブジェクトの権限を確認する
```sh
gsutil acl get gs://$MY_BUCKET_NAME/cat.jpg  > acl.txt
cat acl.txt
```

### オブジェクトへのアクセスを非公開に変更する
```sh
gsutil acl set private gs://$MY_BUCKET_NAME/cat.jpg
```

### 現在使用しているアカウント（ユーザー）の権限を確認
- 表示されたものに「*」が付いている物が適応されているアカウント
```sh
gcloud config list
```

### googlecloudから配布されたjson形式の認証情報を適応する
- サービスアカウントを作成した時にローカルに払い出されたjsonファイルの名前を「credentials.json」に変更する
```sh
gcloud auth activate-service-account --key-file credentials.json
```

###
