```sh
curl \
http://hadoop.apache.org/docs/current/\
hadoop-project-dist/hadoop-common/\
ClusterSetup.html > setup.html

cp setup.html setup2.html
cp setup.html setup3.html

python3 -c 'import base64; import os; print(base64.encodebytes(os.urandom(32)))'
# コマンド出力から b' および \n' を除いて、生成された鍵の値をコピー

gsutil config -n
vi .boto
# [#encryption_keys]で検索してコピーした値を挿入してコメント外す
gsutil cp setup2.html gs://$BUCKET_NAME_1/
gsutil cp setup3.html gs://$BUCKET_NAME_1/
```
