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

# （上の続き）鍵のローテーション
```
vi .boto
# decryption_key1 の「#」を削除してコメントを解除し、現在の鍵を encryption_key 行から decryption_key1 行にコピー

python3 -c 'import base64; import os; print(base64.encodebytes(os.urandom(32)))'
# コマンド出力から b' および \n' を除いて、生成された鍵の値をコピー

vi .boto
# 「encryption_key=」という新しい鍵の値を貼り付け

gsutil rewrite -k gs://$BUCKET_NAME_1/setup2.html
# setup2.html の鍵を書き換え、setup3.html については書き換えない
# これにより、鍵を適切にローテーションさせないとどうなるかがわかる

vi .boto
# decryption_key1 行に再度「#」を追加し、コメントアウト

gsutil cp  gs://$BUCKET_NAME_1/setup2.html recover2.html
gsutil cp  gs://$BUCKET_NAME_1/setup3.html recover3.html
# 2は成功し、3は失敗する
```
