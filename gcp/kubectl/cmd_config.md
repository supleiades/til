- アクティブ コンテキストを出力
```
kubectl config current-context
```

- kubeconfig ファイルの内容を出力
```
kubectl config view
```

- kubeconfig ファイル内のすべてのクラスタ コンテキストの詳細を出力
```
kubectl config get-contexts
```

- アクティブ コンテキストを変更
```
kubectl config use-context {変更したいコンテキスト}
```

- アクティブ コンテキストのクラスタ情報を出力
```sh
kubectl cluster-info
```
