# Ansible Tower
- 略称：　AWX
  - AWXは、Web UIでAnsibleのPlaybookやインベントリーを管理したり、スケジューラー機能を使ってPlaybookを定期実行たり、またその実行結果を確認したりすることができます。
  <img src=https://user-images.githubusercontent.com/45380191/147423653-9710bb18-9240-46a7-97a3-adb753dedbe6.png width=300>


## GitとAWXの呼び名（イメージ）の違い
| AWS | Git | 説明 |
| :- | :- | :- |
| ジョブテンプレート | プロジェクト/Playbook | 基本的な実行単位 |
| プロジェクト | Gitリポジトリ | Playbookの場所 |
| インベントリー | ホストリスト | Ansibleのインベントリーと同義 |
| 認証情報 | ログイン情報 | 制御対象機器へのログイン情報 |
