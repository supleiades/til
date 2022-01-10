```
任意role名/             
|--tasks/   
|--handlers/
|--files/
|--templates/
|--vars/
|--defaults/
|--meta/
```
| ディレクトリ名 | 説明 |
| :- | :- |
| tasks | tasksセクションを記載したファイルを配置 |
| files | デプロイするファイルやスクリプトなどを配置 |
| templates | templateモジュールで利用するjinja2テンプレートを配置 |
| vars | varsセクションを記載したファイルを配置 |
| defaults | デフォルト変数を記載したファイルを配置 |
| meta | メタデータ定義ファイル(特にrole間の依存関係の記述)を配置 |
