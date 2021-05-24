# sftpのログを取得
- sudo vim /etc/ssh/sshd_config
```sh
Subsystem sftp /usr/libexec/openssh/sftp-server -u {umask} -l {log level} -f {log dest}
```
### 参考
- https://kaworu.jpn.org/security/sftp-server
