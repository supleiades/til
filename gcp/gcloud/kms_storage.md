
# 対象バケットの暗号鍵を確認 
gsutil kms encryption gs://$DEVSHELL_PROJECT_ID-kms
# Google管理の鍵の場合このような出力になる
## Bucket gs://qwiklabs-gcp-03-057d4af0f536-kms has no default encryption key

echo "This is sample file 1" > file1.txt
echo "This is sample file 2" > file2.txt
echo "This is sample file 3" > file3.txt

# 暗号しないでアップロード
gsutil cp file1.txt gs://$DEVSHELL_PROJECT_ID-kms

KEYRING_NAME=lab-keyring
CRYPTOKEY_1_NAME=labkey-1
CRYPTOKEY_2_NAME=labkey-2

# KMSはキーリングという箱の下に鍵を保存する感覚
# 鍵の箱作り 
gcloud kms keyrings create $KEYRING_NAME --location us
# 一つ目の鍵作成
gcloud kms keys create $CRYPTOKEY_1_NAME --location us \
--keyring $KEYRING_NAME --purpose encryption
# 二つ目の鍵
gcloud kms keys create $CRYPTOKEY_2_NAME --location us \
--keyring $KEYRING_NAME --purpose encryption

# バケットに二つの鍵を許可する
gsutil kms authorize -p $DEVSHELL_PROJECT_ID -k \
projects/$DEVSHELL_PROJECT_ID/locations/us/keyRings\
/$KEYRING_NAME/cryptoKeys/$CRYPTOKEY_1_NAME
gsutil kms authorize -p $DEVSHELL_PROJECT_ID -k \
projects/$DEVSHELL_PROJECT_ID/locations/us/keyRings\
/$KEYRING_NAME/cryptoKeys/$CRYPTOKEY_2_NAME

# バケットの暗号鍵に一つ目の暗号鍵を紐づける
gsutil kms encryption -k \
projects/$DEVSHELL_PROJECT_ID/locations/us/keyRings\
/$KEYRING_NAME/cryptoKeys/$CRYPTOKEY_1_NAME \
gs://$DEVSHELL_PROJECT_ID-kms

# 鍵を紐づけた後にfile1と同じようなコマンドでアップロード
gsutil cp file2.txt gs://$DEVSHELL_PROJECT_ID-kms

# 二つ目の鍵をアップロードする時に指定して行う（-o）
gsutil -o \
"GSUtil:encryption_key=projects/$DEVSHELL_PROJECT_ID/locations/us/keyRings\
/$KEYRING_NAME/cryptoKeys/$CRYPTOKEY_2_NAME" \
cp file3.txt gs://$DEVSHELL_PROJECT_ID-kms

# オブジェクトの情報を確認
gsutil ls -L gs://$DEVSHELL_PROJECT_ID-kms/file3.txt
