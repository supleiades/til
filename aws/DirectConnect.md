# Direct Connect

## 3つの接続方法

### ホスト型仮想インターフェイス（VIF)
- ホスト型DirectConnect接続ごとに作成できるVIFは1つだけ
- [参考](https://aws.amazon.com/jp/premiumsupport/knowledge-center/direct-connect-types/)


| 名前 | 説明 | 備考 | 手順 |
| :- | :- | :- | :- |
| 標準VIF　| 親DirectConnect接続が存在するAWSアカウント |  |  |
| ホスト型VIF | 同じ親DirectConnect接続を使用している別のAWSアカウント,APNのパートナーから購入したVIF | 標準VIFと同じ方法でパブリックリソースやVPCに接続可能。 | [link](https://docs.aws.amazon.com/directconnect/latest/UserGuide/createhostedvirtualinterface.html) |
| ホスト型接続 |  APNパートナーから購入したsub-1G接続 | APNパートナーから専用の帯域幅がDirectConnectsub-1G接続が割り当てられます。 | [link](https://docs.aws.amazon.com/directconnect/latest/UserGuide/accept-hosted-connection.html) |
