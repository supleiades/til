# Cloud Shellから起動
```
sudo pip3 install -r requirements.txt
python3 main.py
```

# App Engine にデプロイする
```
gcloud app create --region=us-central
gcloud app deploy --version=one --quiet
# --no-promote パラメータは App Engine に対し、引き続き古いバージョンでリクエストを処理するよう指示します
# バージョンを切り替えるにはコンソールから操作
gcloud app deploy --version=two --no-promote --quiet
```

# Kubernetes Engine にデプロイする
```
# コンソールからk8sを新規作成
kubectl get nodes
gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/devops-image:v0.2 .
kubectl apply -f kubernetes-config.yaml
kubectl get pods
kubectl get services
```

# Cloud Run にデプロイする
```
gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/cloud-run-image:v0.1 .
# コンソールからCloudRunを作成し、ImageURLを入れる
```
