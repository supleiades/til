# 基本的な構成ファイルの作成の仕方
## 簡単な構成ファイルの例
```
resources:
- name: myfirstvm
  type: compute.v1.instance
  properties:
    zone: us-central1-a
    machineType: https://www.googleapis.com/compute/v1/projects/[PROJECT_ID]/zones/us-central1-a/machineTypes/f1-micro
    disks:
    - deviceName: boot
      type: PERSISTENT
      boot: true
      autoDelete: true
      initializeParams:
        sourceImage: https://www.googleapis.com/compute/v1/projects/debian-cloud/global/images/debian-9-stretch-v20180105
    networkInterfaces:
    - network:  https://www.googleapis.com/compute/v1/projects/[PROJECT_ID]/global/networks/default
      accessConfigs:
      - name: External NAT
        type: ONE_TO_ONE_NAT
```

## 構成ファイルを作成するにあたって必要な情報の取得
### 使用可能なゾーン一覧表示
`$ gcloud config zones list`
### 使用可能なマシンタイプ一覧表示
`$ gcloud compute machine-types list`
### f1-microマシンタイプのURLを取得
`$ gcloud compute machine-types describe f1-micro --zone us-central1-a | grep selfLink`
### Debianイメージをフィルタリングして表示（その他cent系でも可）
`$ gcloud compute images list | grep debian`
### debian-9イメーのURL取得
`$ gcloud compute images describe debian-9-stretch-vxxxx --project debian-cloud | grep selfLink`
### 使用可能なネットワーク一覧表示
`$ gcloud compute networks list`
### 指定したネットワークのURLを表示
`$ gcloud compute networks describe default | grep selfLink`
### デプロイ
`$ gcloud deployment-manager deployments create my-first-deployment --config my-first-config.yaml`
### デプリメントを削除する（エラー時の対処など）
`$ gcloud deployment-manager deployments delete  my-first-deployment`
