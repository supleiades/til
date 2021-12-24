# Transit Gateway


## TransitGatewayの作成
### パラメータ
| パラメータ | 概要 |
| :- | :- |
| Name tag | 	Nameタグ |
| Description | 	説明 |
| Amazon side ASN | 	Amazon側のBGPセッションのAutonomous System Number |
| DNS support | 	Transit Gateway経由のVPC内のインスタンスからパブリックDNS→プライベートIPの名前解決を有効にするかどうか |
| VPN ECMP support | 	VPN間でEqual Cost Multipath ルーティングが必要な場合に有効化する |
| Default route table association★ | 	デフォルトTransit Gatewayルートテーブルを作成し、新規のアタッチメントに自動的にアソシエーションさせる |
| Default route table propagation★ | 	デフォルトTransit Gatewayルートテーブルを作成し、新規のアタッチメントから自動的にプロパゲーションさせる |
| Auto accept shared attachments★ | 	クロスアカウント のアタッチメントを自動的に承認する |

<img src=https://user-images.githubusercontent.com/45380191/147326495-0f17acea-ac24-472b-b9cc-aee208046c8d.png width=500>





## TransitGatewayを他のアカウントに共有
1. 共有元アカウントで「共有」を作成
1. 共有先アカウントで「共有」を承認


## TransitGatewayのASN
<img src=https://user-images.githubusercontent.com/45380191/147325673-4c3cd0d1-3df0-425c-83ac-d182bb3e32f4.png width=500>


## 用語
| 用語 | 説明 |
| :- | :- |
| アタッチメント | AWS Transit GatewayにAmazon VPCやVPN、AWS Direct Connect Gatewayを関連付ける |
| ルートテーブル | ネットワークトラフィックの経路や行き先を判断する際に使われる |
| アソシエーション | アタッチメントにて関連付けたAmazon VPCなどをルートテーブルに結びつけ、パケットを送信できるようにする事を言います。ただし、アソシエーションは一つのルートテーブルにしか適用出来ない |
| プロパゲーション | アソシエートしたルートテーブルにプロパゲートする事によって経路表ができ、VPC間での通信が可能となる |
| スタティックルート | 管理者が宛先ネットワークへの最適なルートを手動で設定したルートのこと<br>アソシエートされていないAmazon VPCなどにも接続できる |

