- 作成
```sh
RULE_NAME=''
VPC_NETWORK=''
TAG_NAME=''
IP_SOURCE=$(dig +qr +short txt `dig +short TXT _spf.google.com | grep -oE 'include:\S*' | cut -d':' -f2 | xargs` | grep -oE 'ip[46]:\S*'| cut -d':' -f2- | sort | uniq|tr '\n' ',' | sed -e 's/,$/\n/g')

gcloud compute firewall-rules create $RULE_NAME \ 
    --action=allow \
    --rules=tcp:22  \
    --source-ranges=$SOURCE_IP  \
    --network=$VPC_NETWORK  \
    --priority 1000 \
    --target-tags=$TAG_NAME 
```
