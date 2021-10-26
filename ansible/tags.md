## タグが付与されたtaskのみ実行する場合
```
ansible-playbook main.yml --tags "{tag_name}"
```

## 逆に特定のタグのtaskをスキップして実行
```
ansible-playbook main.yml --skip-tags "{tag_name}"
```

# tagsの付与例
- roles
```yml
- hosts: dev
  sudo: yes
  roles:
    - role: apache
      tags: apache
```
- include
```yml
- include: dev.yml tags=dev
```
