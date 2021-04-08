```
gsutil lifecycle get gs://$BUCKET_NAME_1
vi life.json
### 以下をコピペ
{
  "rule":
  [
    {
      "action": {"type": "Delete"},
      "condition": {"age": 31}
    }
  ]
}
###
gsutil lifecycle set life.json gs://$BUCKET_NAME_1
gsutil lifecycle get gs://$BUCKET_NAME_1
```
