# cfn-init, UserData
- インスタンス起動後のソフトウェアインストールやサービス開始などのために使用でき、ミドル~アプリケーションレイヤーまでCloudFormationで自動構築可能にする
- [【初心者向け】CloudFormationヘルパースクリプトを用いて、WebServerを構築してみた](https://blog.serverworks.co.jp/build-web-server-by-cfn#CloudFormation%E3%83%98%E3%83%AB%E3%83%91%E3%83%BC%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88)


## 違い
- コマンドの実行成否がスタックの成否に影響するか否か

| 種類 | 説明 |
| :-- | :-- |
| UserData | コマンドの成否はスタックの成否に影響しないため、定義したコマンドが失敗してもスタックは成功ステータスになる |
| cfn-init | "cfn-signal" と組み合わせることで、定義したコマンドの実行成否はスタックの成否に影響する |
