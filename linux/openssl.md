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

## 中身を見る
```sh
openssl x509 -noout -text -in {csr file} | md5sum
```

## 整合性確認
### 申請書（cs）と秘密鍵（key）
```sh
openssl x509 -noout -modulus -in {csr file} | md5sum
openssl rsa -noout -modulus -in {key file} | md5sum
```

### 証明書（crt）と秘密鍵（key）の基本
```sh
openssl x509 -noout -modulus -in {crt file}
openssl rsa -noout -modulus -in {key file}
```
- 上を見やすくするためにMD5ハッシュを使う
```sh
openssl x509 -noout -modulus -in {crt file} | md5sum
openssl rsa -noout -modulus -in {key file} | md5sum
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
