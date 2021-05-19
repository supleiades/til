```yml
- name: システムロケールの確認
  command: localectl status
  register: localectl_result
  check_mode: no
  changed_when: false

- name: ロケールの変更
  command: localectl set-locale LANG=ja_JP.utf8
  when: "'LANG=ja_JP.utf8' not in localectl_result.stdout"
```
- register とは、タスクの実行結果を指定した変数に代入してくれるディレクティブ
  - command モジュールは、終了コードが0の場合にchangedステータスを返す
  - 何も変更していないのにchangedステータスになるのは違和感を感じる
- changed_when: false として、実行結果のステータスを強制的に変更できる

### 参考
https://goodbyegangster.hatenablog.com/entry/2019/05/02/053303
