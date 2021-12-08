既存ssh_configの情報を使用してhostsを作成・使用せずに対象にコマンドライン(ansibleコマンド)からsshやその他モジュールを使用する

## 前提
- ssh_configに記載したホスト名で対象にsshできること
```sh
ssh {ホスト名}
```


## 準備
- ansible.cfgと同じディレクトリにいること
- ansible.cfgに以下の設定を追加(なければ作成)
```cfg
[ssh_connection]
ssh_args = -F ssh_config
```


## 実行
- 注意
  - ホスト名の後に「,(カンマ)」が必要です
  - 「--connection=local」この引数も必要です
```sh
## ホスト名を任意のものに変更すること　
ansible -i {ホスト名}, all -m ping --connection=local
```

### その他、興味本位なテスト
```sh
## 成功
ansible -i {ホスト名}, all -m ping --connection=local 
# {ホスト名} | SUCCESS => {
#     "ansible_facts": {
#         "discovered_interpreter_python": "/usr/bin/python"
#     },
#     "changed": false,
#     "ping": "pong"
# }


## -以下失敗-----------------------------------------------------
## --connection=localなし
ansible -i {ホスト名}, all -m ping                   
# {ホスト名} | UNREACHABLE! => {
#     "changed": false,
#     "msg": "Failed to connect to the host via ssh: Can't open user config file ssh_config: No such file or directory",
#     "unreachable": true
# }

# allなし
ansible -i {ホスト名}, -m ping --connection=local 
# usage: ansible [-h] [--version] [-v] [-b] [--become-method BECOME_METHOD] [--become-user BECOME_USER] [-K] [-i INVENTORY] [--list-hosts] [-l SUBSET]
#                [-P POLL_INTERVAL] [-B SECONDS] [-o] [-t TREE] [-k] [--private-key PRIVATE_KEY_FILE] [-u REMOTE_USER] [-c CONNECTION] [-T TIMEOUT]
#                [--ssh-common-args SSH_COMMON_ARGS] [--sftp-extra-args SFTP_EXTRA_ARGS] [--scp-extra-args SCP_EXTRA_ARGS]
#                [--ssh-extra-args SSH_EXTRA_ARGS] [-C] [--syntax-check] [-D] [-e EXTRA_VARS] [--vault-id VAULT_IDS]
#                [--ask-vault-password | --vault-password-file VAULT_PASSWORD_FILES] [-f FORKS] [-M MODULE_PATH] [--playbook-dir BASEDIR]
#                [--task-timeout TASK_TIMEOUT] [-a MODULE_ARGS] [-m MODULE_NAME]
#                pattern
# ansible: error: the following arguments are required: pattern


# ,(カンマ)なし
ansible -i {ホスト名} all -m ping --connection=local
# [WARNING]: No inventory was parsed, only implicit localhost is available
# [WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'


```
