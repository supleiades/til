# DNSのレコードの確認
```
# 冗長化されているネームサーバーにそれぞれ同じ設定か確認する時など
dig ns {domain name, ip} @{NX address}}

# NSレコードが更新されているかを結果だけ返す
dig {domain name, ip} ns +short 

# ルートサーバーから目的のドメインまでどの経路で名前解決されたかの一連を表示する
dig {domain name, ip} +trace
```

# dns関連の確認方法
```
dig @8.8.8.8 {target domain} ns +short

dig @{dns server} {target domain} ns +short

whois {target domain} | grep Name
```
