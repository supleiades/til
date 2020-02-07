```
aws kms list-keys
# 鍵一覧表示

aws kms encrypt --key-id "{使用する鍵}" --plaintext 'Hello, world!'
# {
#     "CiphertextBlob": "{Hellow,worldが暗号化された文字列}",
#     "KeyId": "arn:aws:kms:ap-northeast-1:{使用したユーザ名}:key/{使用したKeyID}"
# }

 aws kms decrypt --ciphertext-blob '{Hellow,worldが暗号化された文字列}' --query Plaintext
# Hello, world!
```

decrypt（復号化）で鍵を指定しないのは、暗号化されたものにその情報が含まれている為
