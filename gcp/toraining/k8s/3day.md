# configMap
- 変数をGCP上で保存し、それをconfigmapとして紐づけることでその変数の値をpod内で使用できる
### configMap - secret
- GCP上でマスキングされて表示される
- base64で暗号化されているだけで、簡単に複合できる
- パスワードなど重要なデータを保存するには向いてない
  - 重要なデータの暗号化に関してはSecretManagerを活用する
### namespeace
- podとconfigMapは同じネームスペースの範囲にあたる
- configMapは同じネームスペースしか参照できず、別のネームスペースは参照できない


# IAM
### 定義済みロール
- Googleが特定の役割に追加して新たな権限を必要となった場合、権限追加などの作業をgoogleが担ってくれる
### サービスアカウント
- Googleサービスのサービスアカウントの
- jsonで作成した認証情報のダウンロードしたキーの有効期間はデフォルトで10年に設定されており、更新しないと失効する
### RBAC
- Role Based Access Control (RBAC: ロール ベース アクセス制御)
### RoleBinding
- サービスアカウントとRoleを紐づけるもの

# GKE内で作られたkubernetes固有のリソースについて
- 作成したものたちの情報はGUIで確認できるか
  - 可能
  - 「Kubernetes Engine > Objectブラウザ」にてObjectの種類をRoleに変更して確認することが出来る
  - yamlで作成したRoleについてはkubenetes内で完結するRoleであるため Cloud Consoleの「IAM>Admin > Roles」からの確認は出ない

# プローブ
### liveness
- 稼働していなければ再起動する
### readiness
- ヘルスチェックのエンドポイントを作る
  - readinessプローブの設定を入れる
- コンテナはリクエストを受け入れる準備ができているか
  - 準備できていなければPodにリクエストに送らない


# Operations
### debug
- GCEで動くコードのデバックも可能なのか？
  - https://cloud.google.com/debugger/docs/setup?hl=ja


# Storage
### KubernetesでGoogleサービスを利用する
- 認証情報が必要になる 
  - workloadIdentity
  - serviceAccount




