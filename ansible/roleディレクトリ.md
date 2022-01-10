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
| ディレクトリ名 | 説明 | 備考 |
| :- | :- | :- | 
| tasks | tasksセクションを記載したファイルを配置 | tasksディレクトリは必須になります<br>main.ymlにはtasksディレクティブは書かずに直接taskのリストを記述していくところが注意 |
| handlers | handlersセクションを記載したファイルを配置 | tasks配下にあるYAMLファイルの中でnotifyの指定があるtaskがchangedの結果になった場合に呼びされる |
| files | デプロイするファイルやスクリプトなどを配置 | Ansibleはfilesディレクトリ配下にあるファイルを認識するようになっているため、filesディレクトリからの相対パスで指定することができる |
| templates | templateモジュールで利用するjinja2テンプレートを配置 | Ansibleはtemplatesディレクトリ配下にあるファイルをtemplateモジュールで利用するjinja2テンプレートファイルと認識するようになっているため、templatesディレクトリからの相対パスで指定することができる |
| vars | varsセクションを記載したファイルを配置 | 優先順位がdefaultsよりも高い<br>実行者側には変更してほしくない変数値を設定することが多い |
| defaults | デフォルト変数を記載したファイルを配置 | varsディレクトリ配下のmain.ymlにも変数定義は記述できますが、違いは優先度です。defautsのほうは優先度が低くなりますので、上書きされる想定のデフォルト値として利用する<br>(例: ID、パスワード関連、OSやMWの設定パラメータ等に利用される) |
| meta | メタデータ定義ファイル(特にrole間の依存関係の記述)を配置 | roleの様々なメタ情報(作成者、ライセンス情報、対応platformetc.)や複数のrole間の依存関係を定義したYAMLファイル(main.yml)を配置する<br>role間依存関係は「dependencies」というディレクティブを利用する |
