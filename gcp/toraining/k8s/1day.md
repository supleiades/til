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
### ノードプール
- ノードをまとめたもの
- まとめる条件は同一なサーバースペック
### クラスター
- クラスター管理料金：月間7200円（目安）
#### ゾーンクラスタ
- クラスターが一つのゾーンで管理されている
#### リージョンクラスタ
- クラスターがリージョンで複数のゾーンで冗長されて管理されている

### YAMLファイル
- オブジェクトはYAMLファイルで定義される
  - それをバージョン管理するとよい
- 同じ名前は使えず、前の名前が削除されると使えるようになる
- labelsを使用することでcliから特定のものを操作できる

### podとコントローラーオブジェクト
- ReplicaSet
- Deployment
  - 常に実行を望んでいるものを動かす対象が推奨
- StatefulSet
- DemonSet
- Job

### ネームスペース
-  

### kubectl（きゅーぶこんとろーる）
- ただし、クラスターを作るのはgcloudコマンド
- 作成されたクラスターを操作するのはkubectl
- kubectlについてはkubenetesとGKE違ったプラットフォームであっても同じ処理になる
- 構成ファイル
  - $HOME/.kube/config
- クラスターに接続
```
gcloud container clusters get-credentials standard-cluster-1 --zone us-central1-a --project {projectn_name}
```
- kubectlの構文
```
kubectl [コマンド:実行する処理] [タイプ] [名前] [フラグ]
```
- 主なコマンド
  - get
  - describe
  - exec 
  - logs
  - オブジェクトを作成、表示、削除、エクスポートなど色々なことができる

### バージョンについて
- 一つの例
  - バージョン「レギュラー」を検証環境にしておき、バージョン「ステーブル」を本番環境にしておく
    - すると、先に検証環境で不具合に気づける
    - 安定したバージョンがステーブル（＝本番環境）になるので安心

### Deployment
- deploymentはRepricaSet（PODの数などを指定するファイル）を複数管理するもの
- RepricaSetを切り替えられる
```
Deployment
+- RepricaSet
   +- Pod
```
- 更新する場合は順Podが切り替わり、全て完了すると古いRepricaSetがなくなる

### Service
- フロントエンドのPodとバックエンドのPodとの仲介になるサービス
  - 管理するPodのbackend（ころころ変わるIP）のエンドポイントとなるサービス
- 人間はPodではなくServiceの名称などを知っていればよくなる
- ServiceとPodを紐づけるのはLabelsで行う

### kind: Job
- バッチ処理など繰り返し行う処理などで活用する
- 失敗しても再度実行する
- ジョブの失敗について
  - pod内のconteinerの処理が失敗したとき
  - コンテナがreturnコードが失敗以外を返す時
  - 意図してエラーで終わらせるには、処理の中でreturnで失敗を返すようにするとジョブとして失敗判定になる
#### kind: CronJob
- cronと同じように定期的に実行される処理
- パラメーター
  - startingDeadlineSconds（パラメータ）：を入れることでn分間の失敗を無視する
