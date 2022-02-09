## 複数タグのtaskを実行
```
ansible-playbook -i [インベントリファイル] main.yml -t dev,reboot
```

## タグが付与されたtaskのみ実行する場合
```
ansible-playbook main.yml --tags "{tag_name}"
```

## 逆に特定のタグのtaskをスキップして実行
```
ansible-playbook main.yml --skip-tags "{tag_name}"
```

## 特殊なtag
### always
- 常に実行する
```yml
  tags:
  - always
```
### never
- 常に実行しない
```yml
  tags:
  - never
```

## ansible lintチェックをタスク単位で拒否
```yml
- name: command
  command: {...comannd content...}
  tags:
    skip_ansible_lint
```

## tagsの付与例
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

