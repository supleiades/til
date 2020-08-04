## バケットの作成
- デフォルト
  - ストレージクラス：Multi-Regilnal
  - ロケーション：US

`$ gcloud mb gs://{bucketName}`

## バケットに存在するファイルの「アクセス制御」と「ヘッダー情報」確認
`$ gsutil ls -L gs://{bucket}/{fileName}`
