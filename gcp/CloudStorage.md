## バケットの作成
- デフォルト
  - ストレージクラス：Multi-Regilnal
  - ロケーション：US

`$ gcloud mb gs://{bucketName}`

## バケットに存在するファイルの詳細情報取得
`$ gsutil ls -L gs://{bucket}/{fileName}`
