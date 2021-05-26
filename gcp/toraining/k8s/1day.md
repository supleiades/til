# k8s
## 注意（制限）
- APIは100秒あたり1000件のリクエストまで受けられる
- プロジェクトあたり5つのネットワークまで使用可能

## コンテナレジストリとアーティファクトレジストリの違い
- 使用するならアーティファクトレジストリを使用することを推奨
- アーティファクトレジストリは権限を使用して閲覧許可などを細かく設定できるサービス
- アーティファクトレジストリはコンテナレジストリの上位互換
- コンテナレジストリは終了に向けて進んでいる話もある

## Googleのコンテナ利用実体
- Googleの全てサービスはコンテナを利用している
- 毎週２０億個起動している
- kubenetesの関係図
```md
(google)Brog
+-(OSS)kubenetes
  +-(GCP)GKE
  +-(AWS)EKS
  +-(Azure)AKS
  +-(オンプレ)kubenetes
```
- kubenetesのGCPマネージドサービスであるGKEメリット
  - ネットワークや冗長などのインフラの設計がとても大変になる

## kubenetesアーキテクチャ
### 概念
- clusterで管理
  - clusterの中にmasterとnodeが存在する
    - master：nodeを管理
    - node：
      - nodeの中にpodが存在する
        - pod：アプリケーションを動かす
          - podの中に一つ以上のconteinerが存在する
        - pod同士が疎通することでサービスが動く 
```py
cluster( master -> node(pod(node(conteiner, conteiner, ... ))))
```
- podにIPアドレスが付与される
## kubenetes
### マスター
- kubectl
  - kube-APIserver
    - etcd
    - kube-scheduler
    - kube-cloud-manager
    - kube-controller-manager
### ノード
- kube-APIserver
  - kubelet
  - Kube-proxy 
## GKE
- kube-APIserver内の様々な設定をしなければいけないケースであれば、GKEを使用できなくなる
### マスター
- クラスタのIPくらいしかユーザーが認識できない
