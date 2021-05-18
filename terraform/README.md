# インストール手順
```
#「https://releases.hashicorp.com/terraform/」で調べてDLするURLを指定する
curl -OL https://releases.hashicorp.com/terraform/{好きなバージョン}/{OSのバージョン}

#unzip してコマンドとして配置
sudo unzip {curlしたファイル} -d /usr/local/bin/

#バージョンの確認
terraform -v
```
