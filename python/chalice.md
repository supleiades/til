- （前提）pythonが使える環境
- lambdaやAPIGateway、IAMロールを合わせて作成、

# インストール
`pip install chalice`
- 

## 環境作成
`chalice new-project {プロジェクト名}`
- プロジェクト名でディレクトリが作成される
- app.pyが作成される
  - app.pyを修正
- requirements.txt.が作成される

### デプロイ
`chalice deploy`

### デプロイ済みを削除
`chalice delete`

### ログを確認
`chalice logs -n(--name) {関数名}`
