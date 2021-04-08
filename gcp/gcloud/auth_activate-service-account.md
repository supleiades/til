- 事前にIAMのサービスアカウントから作成（鍵付きで）する必要がある
```
# コンソール上のIAM-サービスアカウント（鍵付き）から作成して出力されたjsonファイルを引数にしてサービスアカウントを認証
gcloud auth activate-service-account --key-file credentials.json
```
