# Deploymentとは
- ReplicaSetでpodを管理するもの

- Deploymentのリストを表示
```sh
kubectl get deployments
```

- レプリカの数を変更する
```sh
kubectl scale --replicas=3 deployment {deployment_name}
```

- （例）Deployment に含まれる nginx のバージョンを更新
```sh
kubectl set image deployment.v1.apps/{deployment_name} nginx=nginx:1.9.1 --record
```

- ロールアウトのステータスを表示
```sh
kubectl rollout status deployment.v1.apps/{deployment_name}
```

- ロールアウト履歴を表示
```sh
kubectl rollout history deployment {deployment_name}
```

- 以前のバージョンにロールバック
```sh
kubectl rollout undo deployments {deployment_name}
```

- Deployment の最新リビジョン
```sh
kubectl rollout history deployment/{deployment_name} --revision=3
```
