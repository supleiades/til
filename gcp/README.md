# インストール前提条件
- Pythonが必須

# gcloudインストール
```
python --version

curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-312.0.0-linux-x86_64.tar.gz

tar xzvf google-cloud-sdk-312.0.0-linux-x86_64.tar.gz

./google-cloud-sdk/install.sh

./google-cloud-sdk/bin/gcloud init
```

# 環境変数化
```
export GCP_PROJECT=`gcloud config list core/project --format='value(core.project)'`
```
