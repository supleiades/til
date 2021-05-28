# configMap
- 変数をGCP上で保存し、それをconfigmapとして紐づけることでその変数の値をpod内で使用できる

### configMap - secret
- GCP上でマスキングされて表示される
- base64で暗号化されているだけで、簡単に複合できる
- パスワードなど重要なデータを保存するには向いてない
  - 重要なデータの暗号化に関してはSecretManagerを活用する

