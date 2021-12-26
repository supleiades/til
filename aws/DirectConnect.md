# Direct Connect

## DirectConnectに接続するには
- AWSがDXのデリバリーを認めた、AWSパートナーと契約するか、ユーザ所有のルータをDirectConnectロケーションに設置する必要がある

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

## Virtual Interface (VIF)
- AWS側の接続先のことを、Direct ConnectではVirtual Interfaceと呼ぶ
- VLANのIDを持つインターフェースの事です。 このVIFによってユーザ環境とAWS環境（VPC）を接続（BGPピアを確立）している

### ３種のVIF
| 名称 | 説明 |
| :- | :- |
| プライベートVIF | VPCにプライベートIPを使って接続（DXを利用するタイプがAWS推奨） 最大10個のVPCと接続が可能。これにより、BGPピアリングのセッション数が減ります。 |
| パブリックVIF | パブリックIPを使って接続。リージョン（中国を除く）を超えた接続が可能で、VPC外のAWSサービス（S3等）にオンプレから直接接続できる。（update: PrivateLinkからS3に接続可能） |
| トランジットVIF | Trangit Gateway用のDirect Connect Gatewayに接続 TrangitGatewayに接続されたVPCを相互に接続が可能 利用できない条件があるので確認が必要|

## 接続の仕方
### DX契約アカウントからVGWを複数作成して複数VPCに分ける
[1つの接続を複数VPCに分ける方法](https://qiita.com/KurokawaKouhei/items/d87e608fe43794bc5738)

## クォータ
- [AWS Direct Connect のクォータ](https://docs.aws.amazon.com/ja_jp/directconnect/latest/UserGuide/limits.html)

## 用語

| 名前 | 略称 | 説明 |
| :- | :- | :- |
| BGPピアリング | - | インターネットに接続する際、オンプレミスのルーターとAWSのルータはBGP(Border Gateway Protocol)により接続し、ルート情報の交換を動的に行います。<br>AWSとユーザの経路情報を動的ルーティングで伝えあってくれるので、通信が出来る |
| Border Gateway Protocol | BGP | ISPが形成する、固有のAS（Autonomous System (自律システム)）が、相互接続時にお互いの経路情報をやり取りするために使われる経路制御プロトコル | 
| Internet Service Provider | ISP | インターネット接続サービスを提供している事業者。上記物理接続の解説部分では、「キャリアと接続」と記載しましたが、このキャリアにあたるのがISPです。 |
| Autonomous System | AS | 自律システム。同じルーティング・ポリシーのもとで動作するルータの集合体のこと。ISPが固有で形成しており、世界中に存在する。| 
