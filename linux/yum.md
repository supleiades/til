##　既にインストールしているパッケージ一覧
```sh
yum list installed 

## 指定
# yum list installed | grep
```


## 管理下のリポジトリを一覧表示
```
yum repolist all
```

## パッケージのバージョンなどを簡単に切り替え
- yum module list {packege_name: php}
```sh
yum module list php
## Last metadata expiration check: 2:35:13 ago on Fri 06 Aug 2021 03:02:01 AM UTC.
## Red Hat Enterprise Linux 8 for x86_64 - AppStream from RHUI (RPMs)
## Name                                              Stream                                               Profiles                                                                ## Summary
## php                                               7.2 [d]                                              common [d], devel, minimal                                              ## PHP scripting language
## php                                               7.3 [e]                                              common [d], devel, minimal                                              ## PHP scripting language
## php                                               7.4                                                  common [d], devel, minimal                                              ## PHP scripting language

Hint: [d]efault, [e]nabled, [x]disabled, [i]nstalled
```

# listとgrep、awkを活用した方法
- (ex)zabbixのgrep結果の名前の部分だけ空白区切りで出力する方法
```sh
yum list installed | grep zabbix | awk '{print $1}' | tr '\n' ' '
```
