# Container Registryにpushする方法
- ①と②は同じ目的を違うやり方で実行している
```
# コマンドの末尾には必ずドット（「.」）を付けてください。ドットは、ソースコードがビルド時に現在の作業ディレクトリ内にあることを指定します。
gcloud builds submit {} .
```
## 共通で使用するファイル
- Dockerfile
```sh
FROM alpine
COPY quickstart.sh /
CMD ["/quickstart.sh"]
```
- quickstart.sh
```sh
#!/bin/sh
echo "Hello, world! The time is $(date)."
```

## ①コマンドラインから指定して実行するパターン
```sh
vi quickstart.sh

vi Dockerfile

chmod +x quickstart.sh

gcloud builds submit --tag gcr.io/${GOOGLE_CLOUD_PROJECT}/quickstart-image .
```
## ②yamlを作成して実行  
```sh
vi cloudbuild.yaml

gcloud builds submit --config cloudbuild.yaml .
```
- cloudbuild.yaml
```
steps:
- name: 'gcr.io/cloud-builders/docker'
  args: [ 'build', '-t', 'gcr.io/$PROJECT_ID/quickstart-image', '.' ]
images:
- 'gcr.io/$PROJECT_ID/quickstart-image'
```
