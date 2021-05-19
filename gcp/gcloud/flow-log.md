- flow-logを有効化
```
gcloud compute networks subnets update default \
--region us-central1 --enable-flow-logs
```

- flow-logを無効化
```
gcloud compute networks subnets update default \
--region europe-west1 --no-enable-flow-logs
```
