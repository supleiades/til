# コマンドラインで対応
```
ansible-playbook -i {inventory filepath} {playbook.yml} --connection=local
```

# ファイル内に記述 
```yml
---
- hosts: local
  connection: local
```


### 参考
https://qiita.com/wildmouse/items/316d15765e5886fa4654
