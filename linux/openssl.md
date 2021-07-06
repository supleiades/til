- SSL/TLS通信込み
```sh
openssl s_client -connect {ip}:{port}
```

## 申請書(csr)の内容を確認する
- csrファイルを作成するために使用した情報と比べて値の正常性確認
```sh
CSRFILE="{csr file}"
openssl req -noout -text -in ${CSRFILE}

# 確認項目6点を変数にセット
SUBJECT_C=
SUBJECT_ST=
SUBJECT_L=
SUBJECT_O=
SUBJECT_OU=
SUBJECT_CN=

# コンソール上でキーワードが赤く表示されていることを確認（grep使用）
openssl req -noout -text -in ${CSRFILE} | grep ${SUBJECT_C}
openssl req -noout -text -in ${CSRFILE} | grep ${SUBJECT_ST}
openssl req -noout -text -in ${CSRFILE} | grep ${SUBJECT_L}
openssl req -noout -text -in ${CSRFILE} | grep ${SUBJECT_O}
openssl req -noout -text -in ${CSRFILE} | grep ${SUBJECT_OU}
openssl req -noout -text -in ${CSRFILE} | grep ${SUBJECT_CN}
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
### 申請書（csr）と秘密鍵（key）
```sh
openssl req -noout -modulus -in {csr file} | md5sum
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
