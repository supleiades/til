# 認証情報(credential)情報の切り出し
- 環境変数を利用
- Terraformの変数の利用
  - Terraformコマンドのオプションで値を渡す
  - 環境変数で値を渡す
  - ファイルで値を渡す（推奨）

## terraform.tfvars
- 参考URL: https://learn.hashicorp.com/terraform/getting-started/variables.html


## コマンド
- terraform validate: Terraformの設定ファイルを含む作業ディレクトリを初期化
- terraform fmt:
- terraform plan: リソースやパラメータを変更することなく、パラメータレベルで変更点を確認
  - terraform plan -destroy: 削除する対象を確認
- terraform apply: 設定ファイルに従ってリソースを作成
- terraform destroy: Terraformが管理するリソースを削除します
- terraform show: terraform.state ファイルを元に現在のリソースの状態を参照

## tfstate ファイル
- ファイル構成
  - terraform.state: （超重要)作成されたリソースに関連する情報が保存される
  - terraform.state.backup: 2度目以降の実行後には、1世代前のものの情報が保存される
- 変更範囲を指定する
  - 本番、ステージ、開発環境のように分かれている場合、変更範囲をこのファイルで指定する

