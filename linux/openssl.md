- SSL/TLS通信込み
```sh
openssl s_client -connect {ip}:{port}
```

## 証明書の有効期限を確認
```sh
openssl x509 -dates -in {crt file}
# notBedore
# notAfter
openssl x509 -dates -in {crt file}
# notBedore
openssl x509 -dates -in {crt file}
# notAfter
```

## 整合性確認
### 証明書（crt）と秘密鍵（key）の基本
```sh
openssl x509 -noout -modules -in {crt file}
openssl x509 -noout -modules -in {key file}
```
- 上を見やすくするためにMD5ハッシュを使う
```sh
openssl x509 -noout -modules -in {crt file} | md5sum
openssl x509 -noout -modules -in {key file} | md5sum
```

### 証明書（CRT）と中間証明書（ca）でハッシュオプションを使って
```sh
openssl x509 -issuer_hash -noout -in {crt file}
openssl x509 -subject_hash -noout -in {ca file}
# hexadecimal(?)
```

- 人間が理解できる表示にした場合
```sh
openssl x509 -issuer -noout -in {crt file}
openssl x509 -subject -noout -in {ca file}
# str
```
