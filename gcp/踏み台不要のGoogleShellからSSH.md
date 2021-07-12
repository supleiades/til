- 踏み台サーバーの費用削減のため
```sh
# ネットワーク作成
gcloud compute networks create vpc-iap-test --subnet-mode=custom
gcloud compute networks subnets create private-subnet --network vpc-iap-test --range 192.168.1.0/24 --region asia-northeast1

# IAP経由でSSH接続するためのFirewallルール作成
gcloud compute firewall-rules create allow-iap-tunnel-ssh \
  --network=vpc-iap-test \
  --allow=tcp:22 \
  --target-tags iap-tunnel-ssh \
  --source-ranges=35.235.240.0/20

# インスタンス作成
gcloud compute instances create my-private-instance \
  --machine-type=f1-micro \
  --zone asia-northeast1-a \
  --subnet=private-subnet \
  --private-network-ip=192.168.1.10 \
  --tags=iap-tunnel-ssh \
  --no-address \
  --boot-disk-size=10GB \
  --metadata=enable-oslogin=TRUE

# SSH接続
gcloud compute ssh my-private-instance
```
