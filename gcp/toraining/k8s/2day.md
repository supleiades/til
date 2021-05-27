## コンテナとは
### 特徴（一部）
- 説明
  - cgroup(ControllGroup)：コンテナ外から中を制御する
  - namespeace(名前空間)：コンテナ内から外へのアクセスを制御
- 特徴
  - クラスターを管理
  - アプリを常に動かしてくれる
  - コンテナ間の通信を制御

### メリット
1. 環境ごと持ち運べること
1. 軽いこと

## クラスターについて
### ポッドシストラクションバゲット
- 参考: https://kubernetes.io/docs/concepts/workloads/pods/disruptions/#pod-disruption-budgets


### ノードを削除できないPodの条件
1. コントローラーで実行されていない
  - kind: Podで作られているもの
1. ローカルストレージを使用している
  - アノテーションを使っているもの
1. 制約ルール（Affinity）による制限
  - Podが他の行先がない、いけない場合
  - どのNodeに配置されるか、特定のコンピューターリソース(Node)でのみ動かしたい場合に使用する
    - あffinity 

###　自動スケーリングされたクラスタのベストプラクティス
- 非推奨
  - マスターのkubeAPIを経由しない操作をすること
- 推奨
  - Podの適切なリクエストを指定
  - PodDisruptionBudgetを使用して可用性を維持###

### node affinity
- affinity
- anti affinity

### Pod
- VPC内のsubnetのIP帯から割り振りされる
- aliace ipを利用してIP範囲を確保する
  - サービス：/20
  - ノード　：/24
    - /24で確保されたIPの中から上限110個使用される
  -　ポッド　：/14
#### ネットワークポリシー
- 設定方法
  - ネットワーキング > ネットワークポリシーの有効
- Pod間のアクセスを制限できる
- ラベルなどを使用して制限する方法がある（IPでもできるようだ）
- kind :NetworkPolicy
  - yamlファイルで指定する必要がある

![image](https://user-images.githubusercontent.com/45380191/119776783-53b1d280-bf00-11eb-9e97-7f1d13f95397.png)
### クラスター内の通信
- クラスターIP：クラスター内からの通信のみで使用する
  - kind: Service
    - 特段指定しない場合のデフォルトでClusterIPになる
    - pod作成時に環境変数としてServiceのIPが登録される
#### kubernetes DNS
- サービスが作成されると自動で名前とIPを関連付けてくれる
- ポッドはサービス名だけで通信できる
- レコードタイプ：A

### クラスター外の通信
- NodePort Service
- ポッドの増減を気にしないで済む
- クラスター外部からクラスター内部への通信を可能にする

### ノードに対しても柔軟に対応
- Loadbalancer Service
- ノードの増減を気にしないで済む
- 外部からのアクセスをNodePortに割り振る

### ingress　HTTP loadbalancer
- これを作ると、google Load balancerが構築される
- 送信先
  - Node Port
  - Node Loadbalancer
- ホストベースやパスベースでリクエストを振り分ける
- IAP、Armor、CDNなどと連携できる

### GKEにおいて
Node＝GCE
ingress=L7ロードバランサー

### ネットワークエンドポイントグループ(neg)
- Pod IPを直接登録できる

### emptyDir
-  Pod 用の一時的なディスク領域として利用可能であり、Pod が terminate されると削除

### インフラとアプリを切り分けて、環境依存しないyamlに
#### persistentVolume
- 永続ディスクのボリューム
#### PersistentVolumeClaim
- persistentVolumeとPodを紐づける設定
- yamlで記述したボリュームの条件とマッチ（要求するボリューム値以上）すれば自動でアタッチされる
- マッチしなければ自動で必要な値で作成される

---------
