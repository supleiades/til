# DNSのレコードの確認
```
# 冗長化されているネームサーバーにそれぞれ同じ設定か確認する時など
dig ns {domain name, ip} @{NX address}}

# NSレコードが更新されているかを結果だけ返す
dig {domain name, ip} ns +short 

# ルートサーバーから目的のドメインまでどの経路で名前解決されたかの一連を表示する
dig {domain name, ip} +trace
```
