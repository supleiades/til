## sshのホスト名保管
- .bashrc か .bash_profile に以下を追記
``` 
function _compreply_ssh(){
  COMPREPLY=(`cat ~/.ssh/config | grep -i -e '^host' | cut -d " " -f 2 | grep -E "$2"`)
}
complete -F _compreply_ssh ssh
```
- [exec $SHELL]コマンドを実行する

### 参考サイト
https://qiita.com/albyte/items/aef1e54fccdcc7e32969
