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

