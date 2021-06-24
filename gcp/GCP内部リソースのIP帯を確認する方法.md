- firewall ruleを作成するときの参考
```
dig +qr +short txt `dig +short TXT _spf.google.com | grep -oE 'include:\S*' | cut -d':' -f2 | xargs` | grep -oE 'ip[46]:\S*'| cut -d':' -f2- | sort | uniq|tr '\n' ',' | sed -e 's/,$/\n/g'
```
