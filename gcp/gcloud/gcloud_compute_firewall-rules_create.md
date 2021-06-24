- 作成
```sh
RULE_NAME=''
VPC_NETWORK=''
TAG_NAME=''
IP_SOURCE=$(dig +qr +short txt `dig +short TXT _spf.google.com | grep -oE 'include:\S*' | cut -d':' -f2 | xargs` | grep -oE 'ip[46]:\S*'| cut -d':' -f2- | sort | uniq|tr '\n' ',' | sed -e 's/,$/\n/g')

gcloud compute firewall-rules create RULE_NAME --action=ALLOW --allow=tcp:22 --source-ranges=[${IP_SOURCE}] --network=VPC_NETWORK --target-tags=TAG_NAME
```
