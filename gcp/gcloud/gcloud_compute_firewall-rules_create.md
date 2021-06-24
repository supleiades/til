- 作成
```sh
RULE_NAME=''
VPC_NETWORK=''
TAG_NAME=''

gcloud compute firewall-rules create RULE_NAME --action=ALLOW --allow=tcp:22 --source-ranges=[``] --network=VPC_NETWORK --target-tags=TAG_NAME
```
