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
  - デフォルトは「/etc/ansible/hosts」
