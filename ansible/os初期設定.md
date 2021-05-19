## selinux
https://docs.ansible.com/ansible/2.9_ja/modules/selinux_module.html
```yml
# 無効化する
- name: Disable SELinux
  selinux:
    state: disabled
```
