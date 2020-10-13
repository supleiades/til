# ssh_configを活用したリモートへのansible実行

Ansibleディレクトリ 配下に[ ssh_config ]を記述し、
[ ansible.cfg ]でssh_configを指定するように記述し、
inventoriesのhostsにssh_configで指定したHostnameを
記述する。コマンドラインから-iでinventoriesファイルを指定する
```
### ssh_config
Host mo9mo9
  Hostname  {ip/hostname}
  IdentityFile {path}
  User  {loginname}

### ansible.cfg
[ssh_connection]
ssh_args = -F ssh_config

### 
[production]
{Hostname of ssh_config}
```
