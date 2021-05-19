- 自分のEIPを確認、環境変数化
```
ip=$(curl -s https://api.ipify.org)
echo "My External IP address is: $ip"
```
- ファイアウォール作成
```
gcloud compute firewall-rules create \
mynetwork-ingress-allow-ssh-from-cs \
--network mynetwork --action ALLOW --direction INGRESS \
--rules tcp:22 --source-ranges $ip --target-tags=lab-ssh
```
- ファイアウォールをインスタンスにアタッチ
```
gcloud compute instances add-tags mynet-eu-vm \
    --zone europe-west1-b \
    --tags lab-ssh
```
- アタッチしたインスタンスにSSHしてみる
```
gcloud compute ssh qwiklabs@mynet-eu-vm --zone europe-west1-b
```


- 同じGCPのリソースにpingを内部的に打つ
```
 ping mynet-eu-vm.europe-west1-b.c.[PROJECT_ID].internal
```
