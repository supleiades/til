```
# リストを表示
gcloud compute zones list | grep us-central1

# ゾーンを設定
gcloud config set compute/zone us-central1-b

# GCEを作成
gcloud compute instances create "{instance_name}" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image-family "debian-10" \
--subnet "default"
```
