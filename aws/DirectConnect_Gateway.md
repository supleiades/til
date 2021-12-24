# Direct Connect Gateway ( DXGW )

## DXGWを利用する場合
- １つのVIFに対して複数のVPCを利可能
  - VPCに作成したVGWをDXGWに関連付けるだけで利用する事が出来る
- (制約)DXGWを介してVGWからVGWへの通信（VPC同士の通信）は出来ない

<img src=https://user-images.githubusercontent.com/45380191/147323988-fe30747c-1563-44ad-a7d4-2d8cc43cd338.png width=500>

## DXGWを利用しない場合
- VIFとVGWは同一リージョンに1対1で設定するという制約がある
  - 別のVPCを利用するたびにVIFの申請が必要になる
  - VPC毎に通信を完全に分けたい場合は有効

<img src=https://user-images.githubusercontent.com/45380191/147323998-78a995c1-e79c-4558-b19c-033ea3a67589.png width=500>

