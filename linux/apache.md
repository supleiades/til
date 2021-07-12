```sh
yum info httpd
yum -y install httpd
httpd -version
systemctl enable httpd.service
systemctl start httpd.service
systemctl status httpd.service

## 停止したい場合
systemctl stop httpd.service
```

# firewall関連
```sh
systemctl stop firewalld

## 80盤ポートの許可
firewall-cmd --add-service=http --zone=public --permanent
firewall-cmd --reload
```
