 ```
gsutil versioning get gs://$BUCKET_NAME_1
gsutil versioning set on gs://$BUCKET_NAME_1
gsutil versioning get gs://$BUCKET_NAME_1
```

# ファイルをバージョン管理してみる
- -v バージョニング オプションを指定
```
ls -al setup.html
vi setup.html
# 適当な行を５行ほど削除してファイルサイズを変える
gsutil cp -v setup.html gs://$BUCKET_NAME_1
vi setup.html
# 適当な行を５行ほど削除してファイルサイズを変える
gsutil cp -v setup.html gs://$BUCKET_NAME_1
gsutil ls -a gs://$BUCKET_NAME_1/setup.html
export VERSION_NAME=<バージョン名をここに入力>
echo $VERSION_NAME
# ex) gs://BUCKET_NAME_1/setup.html#1584457872853517
gsutil cp $VERSION_NAME recovered.txt
ls -al setup.html

ls -al recovered.txt
```
