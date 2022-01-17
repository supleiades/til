# Amazon Inspector

## コンソール画面の違い
1. Inspector v1( Amazon Inspector Classic )  
https://ap-northeast-1.console.aws.amazon.com/inspector/home?region=ap-northeast-1#/dashboard
1. Inspector v2 ( Amazon Inspector )  
https://ap-northeast-1.console.aws.amazon.com/inspector/v2/home?region=ap-northeast-1#/dashboard


## Inspector v1とv2の違い
- 疑惑の部分あり

| 項目 | v1 | v2 |
| :-- | :- | :- |
| エージェント | 基本InspectorAgentから詳細情報取得 | SsmApentから情報取得 |

```md
Q: Amazon Inspector は Amazon Inspector Classic とどのように異なりますか?

Amazon Inspector は、新しい脆弱性管理サービスを創出するために再設計および再構築されました。Amazon Inspector Classic で強化された主な点は次のとおりです。
スケールを考慮した構築: 新しい Amazon Inspector は、スケールと動的なクラウド環境を考慮して構築されています。一度にスキャンできるインスタンスまたはイメージの数に制限はありません。
コンテナイメージのサポート: 新しい Amazon Inspector は、Amazon ECR にあるコンテナイメージもスキャンして、ソフトウェアの脆弱性を検出します。コンテナ関連の結果も ECR コンソールにプッシュされます。
マルチアカウント管理のサポート: 新しい Amazon Inspector は AWS Organizations と統合されているため、組織の Amazon Inspector の管理者アカウントに委任できます。この委任された管理者 (DA) アカウントは、すべての結果を統合し、すべてのメンバーアカウントを設定できる一元化されたアカウントです。
AWS Systems Manager Agent: 新しい Amazon Inspector を使用すると、すべての Amazon EC2 インスタンスにスタンドアロンの Amazon Inspector エージェントをインストールして維持する必要がなくなります。新しい Amazon Inspector は、広くデプロイされている AWS Systems Manager Agent (SSM Agent) を使用しており、その必要性を排除しています。
自動化された継続的なスキャン: 新しい Amazon Inspector は、新しく起動されたすべての Amazon EC2 インスタンスと Amazon ECR にプッシュされた適格なコンテナイメージを自動的に検出し、ソフトウェアの脆弱性と意図しないネットワークのエクスポージャーを即座にスキャンします。 新しい脆弱性をもたらす可能性のあるイベントが発生すると、関連するリソースが自動的に再スキャンされます。リソースの再スキャンを開始するイベントには、EC2 インスタンスへの新しいパッケージのインストール、パッチのインストール、およびリソースに影響を与える新しい一般的な脆弱性と暴露 (CVE) がパブリッシュされた際などがあります。
Inspector リスクスコア: 新しい Amazon Inspector は、最新の CVE 情報を、ネットワークのアクセス可能性や悪用可能性の情報などの時間的および環境的要因と相関させて、結果の優先順位付けに役立つコンテキストを追加することにより、Inspector のリスクスコアを計算します。
```

## プライベートな環境にあるEC2から情報取得したい
### v2
- ssmエンドポイント(interface)を3つ作成
  - com.amazonaws.[region].ssm
  - com.amazonaws.[region].ec2messages
  - com.amazonaws.[region].ssmmessages
- s3エンドポイント(gateway)を1つ作成
  - com.amazonaws.[region].s3
- 対象のEC2インスタンスにSSMエージェントを導入する
  - デフォルトでプリインストールされているOSについて
    - パラメータストア > パブリックパラメータ  
      - [Amazon Linux OSの最新AMI](https://ap-northeast-1.console.aws.amazon.com/systems-manager/parameters/?region=ap-northeast-1&tab=PublicTable#public_parameter_service=ami-amazon-linux-latest)
      - [Windows OSの最新AMI](https://ap-northeast-1.console.aws.amazon.com/systems-manager/parameters/?region=ap-northeast-1&tab=PublicTable#public_parameter_service=ami-windows-latest)
    - [SSMAgentは、特定のAmazonMachineImages(AMIs)で作成されたインスタンスにプレインストールされています](https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/prereqs-ssm-agent.html)

.
