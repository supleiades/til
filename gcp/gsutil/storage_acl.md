```
export BUCKET_NAME_1=<バケット名 1 をここに入力>

echo $BUCKET_NAME_1
curl \
http://hadoop.apache.org/docs/current/\
hadoop-project-dist/hadoop-common/\
ClusterSetup.html > setup.html

gsutil cp setup.html gs://$BUCKET_NAME_1/
gsutil acl get gs://$BUCKET_NAME_1/setup.html  > acl.txt
cat acl.txt

gsutil acl set private gs://$BUCKET_NAME_1/setup.html
gsutil acl get gs://$BUCKET_NAME_1/setup.html  > acl2.txt
cat acl2.txt

gsutil acl ch -u AllUsers:R gs://$BUCKET_NAME_1/setup.html
gsutil acl get gs://$BUCKET_NAME_1/setup.html  > acl3.txt
cat acl3.txt
```
