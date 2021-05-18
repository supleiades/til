# 実行環境構築手順
- 事前準備
  - pythonの実行環境が必要
```
python3 -m venv venv
pip install ansible
```


# ansible-playbook
### オプション
- -i： インベントリファイルのパスを指定
  
# オプションの説明
```sh
# -iでインベントリファイルを指定
## デフォルトは「/etc/ansible/hosts」
# -uでSSH接続するリモートユーザー名を指定
# -tで指定したタグが付けられたタスクのみを実行
# --private-keyでSSHの秘密鍵を指定
# SSHは公開鍵認証でも、一般ユーザーがsudoを実行するには-k(--ask-pass)オプションもつける
ansible-playbook -i hosts playbook.yml -u wkuser -t mysql-after --private-key=~/.ssh/id_rsa -k
```
