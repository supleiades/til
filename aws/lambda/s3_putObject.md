# about
- トリガーにEventBridgeを使い自動でファイルを作成する処理

## lambda-habdler.py
```py
import os
import boto3
from datetime import datetime
 
print('Loading function')      
s3 = boto3.resource('s3')      # S3オブジェクトを取得
 
# ④Lambdaのメイン関数
def lambda_handler(event, context):
    
    bucket = '{bucketname}'    # バケット名を指定
    to_dir_path = '{dirpath}'   # 指定のディレクトリのパス（があれば）指定
    file = 'test_' + datetime.now().strftime('%Y-%m-%d-%H-%M-%S') + '.txt'  # ⑥オブジェクトのキー情報を指定
    key = os.path.join(to_dir_path, file)
    print(key)
    file_contents = 'Lambda test'  # ファイルの内容
    
    obj = s3.Object(bucket, key)     # バケット名とパスを指定
    obj.put( Body=file_contents )   # バケットにファイルを出力
    return
```

## S3の権限
- アクセスポリシーの参考
```json
{
  "Id": "{}",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "{}",
      "Action": [
        "s3:PutObject"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::{}",
      "Principal": {
        "AWS": [
          "arn:aws:iam::{}"
        ]
      }
    }
  ]
}
```
