# Direct Connect

## 3つの接続方法
- ホスト型DirectConnect接続ごとに作成できるVIFは1つだけ
- [参考](https://aws.amazon.com/jp/premiumsupport/knowledge-center/direct-connect-types/)


| 名前 | 説明 | 備考 | 手順 |
| :- | :- | :- | :- |
| 標準VIF　| 親DirectConnect接続が存在するAWSアカウント |  |  |
| ホスト型VIF | 同じ親DirectConnect接続を使用している別のAWSアカウント,APNのパートナーから購入したVIF | 標準VIFと同じ方法でパブリックリソースやVPCに接続可能。 | [link](https://docs.aws.amazon.com/directconnect/latest/UserGuide/createhostedvirtualinterface.html) |
| ホスト型接続 |  APNパートナーから購入したsub-1G接続 | APNパートナーから専用の帯域幅がDirectConnectsub-1G接続が割り当てられます。 | [link](https://docs.aws.amazon.com/directconnect/latest/UserGuide/accept-hosted-connection.html) |

### 標準 VIF（専有型）
<img src=https://user-images.githubusercontent.com/45380191/147321741-34da56ff-6d8b-409e-a4db-71e97fc1eb79.png width=500>

### ホスト型 VIF（共有型）
- AWSDirectConnect> 接続(connect)の画面では何も表示されず、かそうインターフェイス(VIF)の画面に表示される

<img src=https://user-images.githubusercontent.com/45380191/147321760-35e5879d-2b60-4347-a3f6-b509e242a76c.png width=500>

### ホスト型接続(sub-1G)
- APNより仮想的なConnectionが提供され、帯域保証されたVIFを1つだけ作成可能

<img src=https://user-images.githubusercontent.com/45380191/147322489-2bb98a37-0e4b-45a2-83bd-a1f711ea6a26.png width=500>
