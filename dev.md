# 間違えた問題


# Lambda
## 環境変数と暗号化のカスタマイズ
キー設定：KMSの鍵を使用しない場合は、lambdaが作成する「aws/lambda」という鍵を使用する
暗号化ヘルパー：環境変数の最大サイズは512MB(1MBは暗号化SDKを使用する)
## 関数のパッケージが大きすぎることで起きるエラーの回避
Lambdaレイヤーを利用してLambda関数の依存関係をアップロードする
## 非同期でLambdaを実行する
InvokeAPIを使ってLambdaを呼び出す
InvocationTypeをEventにするとLambda関数を非同期に呼び出せる
## SQSキューに送信する前に、Lambda関数を2回施行する対応
lambda関数のDeadLetterConfigパラメータでSQSのARNを指定
## Lambda関数にXーRay実行に必要なファイルを配置してデータをX-Rayに送信する
Lambda X-Rayトレースを有効化する(トレースする場合X-Rayデーモンは自動的に実行される)
## Lambda関数でバンドルして依存関係を設定
Lambda関数と依存関係を1つのフォルダでZIP化する
## サイズの制限
展開パッケージのサイズ制限: 250MB
/tmpディレクトリのサイズ制限: 512MB
回答されたパッケージが250MBを超えてしまう場合、250MB以下としてアップロードし、余分ファイルは/tmpでロードする
## インターネットに接続
起動されるVPC内にNATインスタンス or NATゲートウェイを設定
関連付けられたSGのautoバウンドを許可
## ロールバック可能かつ、ユーザーのちゅだんを防ぎ、新しいバージョンを展開するのに最適なオプション
Lambda関数エイリアスにトラフィック処理を設定する
## X-Rayデーモンとの通信を用意にするための環境変数
_X_AMZN_TRACE_ID: トレースヘッダーが受信された場合、トレースIDおよび親セグメントIDなどが環境に入力される
AWS_XRAY_CONTENT_MISSING: トレーシングヘッダーが私用出来ない場合の動作を指定。デフォルトはLOG_ERROR
## Invoke(呼び出し)APIの3種のInvokeInvocationType
RequestResponse(デフォ): 関数を同期的に呼び出す
Event: InvocationTypeにEventを指定すると非同期実行になる
DrRun: パラメータ値の検証、ユーザーまたはロールに関数の実行権限があるかどうか確認
## 実行コンテキストを再利用するため、初回時と更新した後の実行時に遅延が発生する
実行コンテキストを使用して、コードにロジックを追加して接続前に接続が存在するかどうかを確認する

# ECS
## タスク定義
コンテナがホストコンテナ・インスタンスポートにアクセスしてポートマッピングを使用してトラフィックを受信できるようにするために必要な設定
## Faragate起動モードでX-Rayデーモンを実行するためのセットアップ方法
X-Rayデーモンエージェントを再度コンテナとしてデプロイ
X-RayにFaragateを操作する適切なIAMロールをタスクに設定
## アプリのパフォーマンスに影響を与えるサービスとパスの特定を行うには
X-Rayデーモンを実行するDockerイメージを作成し、イメージリポジトリにアップロードしてECSクラスターにデプロイする
タスク定義ファイルでポートマッピングとネットワークモード設定を構成してUDPポート2000でのトラフィックを許可
※X-RayデーモンはUDP2000でトラフィックをリッスンする
## ECSの機能で特定の属性のコンテナインスタンスをグループ化するには
クラスタークエリ言語
## リソースへのアクセス許可
タスクの分割は各IAMロールを分割してアタッチすることで行う
## セカンドクラスターのパラメータ入力を使用してテンプレートを再起動したが、別前インスタンスでメインクラスターで起動された原因
ブートストラップ中にクラスタ名のパラメータがファイル[ /etc/ecs/ecs.config ]に反映されていない
## タスク配置戦略
binpack: 使用可能な最小量のCPUまたはメモリに基づいて配置することにより、使用中のインスタンス数を最小限に抑える
random: タスクをランダムに配置。暗黙的や明示的に指定した制約を尊重する
spread: 指定された値に基づいてタスクを均等に配置。

# CloudFront
## HTTPS通信のみに対応した設定
CloudFrontのビューアプロトコルポリシー にReadirect HTTP to HTTPSを設定する
CloudFrontのビューアプロトコルポリシーにHTTPS Onlyを設定する
## RTMP
Adobe Flashマルチメディアを提供する際に使用する

# ElasticBeanstalk
## cron.yaml
定期ジョブを追加するためのファイル
## .ebextensions
設定ファイルを配置するフォルダ
### .config
YAML or JSON形式の設定ファイル
## env.yaml
アプリ環境の環境名、ソリューションスタック、環境リンクを設定するソースバンドルに追加する構成ファイル
環境作成や更新する場合(グループ名)--group-nameか--env-group-suffixで指定
## サービスに保存できるバージョン数の制限・管理
ライフサイクルポリシー
## リソースの全容量を維持するデプロイ方法
Rolling with additinal batch
Immutable
## デプロイ時に利用するサービス
CodePipeline
CloudFotmation
## X-Rayデーモンの有効化
(コンソール)デーモンを自動的に実行する設定オプションで有効化するとインスタンスに自動でインストールされる
(.ebextensions)xray-daemon.config構成ファイルを含める事でX-Rayを有効化
## 本番環境と負荷テスト用のバージョンを用意したい
本番環境と同じ構成をした環境設定を追加する

# APIGateway
## ステージ変数
各リソースで設定することでリリースの段階を管理できる
## 接続拒否エラーの原因
HTTPSエンドポイントのみ公開する(=HTTPをサポートしていない)
## 504エラー
APIGatewayでINTEGRATION_TIMEOUTエラー
Lambdaファンクションが29秒以上実行できずにAPIGatewwayがタイムアウトエラー
## REST APIを実装に使用できるサービスの組み合わせ
API Gateway + Lambda
ALB + ECS
## 統合タイプ
Lambdaプロキシ統合: AWS_PROXY
Lambdaカスタム統合およびその他全てのAWS統合: AWS
HTTPプロキシ統合およびHTTP統合: HTTP_PROXY or HTTP
モック統合: MOCK
## リリースのデプロイをテストする方法
APIGateway Canaryリリース
## ステージへのデプロイ
APIを更新するためたびに、既存ステージor新しいステージにAPIを再デプロイする必要がある
## 認証方式
トークンベースのLambda(Token)オーソライザー: OAuthトークンなどのべアラートトークンで発信者IDを受け取る
リクエストパラメータベースのLambda(Request)オーソライザー: ヘッダー、クエリ文字列、stageVaribles、$
## APIメソッドでバックエンドサービスにリクエストするためにクライアントが実行しなければいけない操作を定義
リソースのメソッドリクエストをセットアップ
## Cloudwatchで使用するメトリクス
１分感覚でCloudWatchに送信される
CacheHitCount: 指定された期間内にAPIキャッシュから配信されたリクエスト数
CacheMissCount: APIキャッシュが有効になっている特定の期間に、バックエンドから提供されたリクエスト数
## オンプレで使用するアプリをLambdaとAPIGatewayに移行する
コンソール上からSqaggerまたはOpenAPI定義をAPIGatewayにインポートする
### SwaggerとOpenAPIとは
Swagger: RESTfulAPIを構築するオープンソースのフレームワーク
OpenAPI: swaggerをベースにして拡張機能を持たせたもの
## 最新のデータを取得したいため、キャッシュエントリを無効にする設定
APIGatewayのコンソールで[Require authorization]チェックボックスをon
クライアントにCache-Control: max-age=0ヘッダーを設定
キャッシュのデフォルトのTTL値を0に設定

# X-Ray
## 特定のデータを認識する時にアノテーションを利用して解析したい
X-Rayコンソールからフィルタ式を選択
GetTraceSummariesAPIを使用して、特定の情報に関連づけられた対象を検索する
## 使用する際の考慮事項
サブセグメントを作成してAWSサービスとSDKで作成するリソースへの呼び出しを記録できる
メタデータオブジェクトをセグメントに保存する追加のカスタムデータを設定する
※BatchGetTrancesAPIで返された完全なセグメントドキュメントでメタデータを表示できる
## 検索やフィルタリングするためにトレースにインデックスをつける方法
Annotation(注釈)を使用して追加情報を記録できる
## コンソールを使用しないでアプリのトレースを表示する
GetTraceSummaries APIを使用してアプリのトレースIDのリストを取得
BatchGetTraces APIを使用してトレースのリストを取得
## PutTracesSegments API
セグメントドキュメントを直接X-Rayに送信する
## セグメントドキュメントをX-Rayに直接送信するカスタムコードの開発のために必要なもの
サブセグメント: これを利用してSDKで作成するリソースの呼び出し、HTTPウェブAPIの呼び出し、SQLクエリの呼び出し記録をする
## 

# S3 Slect
オブジェクトのコンテンツをフィルターして必要なデータのサブネットのみ取得する
SQLステートメントを使用する

# AutoScaling
## Desired capacity
手動で現在のインスタンス数を増やせる
※[Desired]の値が[Max]よりも大きい場合は[Max]を修正する必要あり

# DynamoDB
## 特定の属性を部分的に取得するための設定
Queryメソッド内のProjectionExpression
## DynamoDBトランザクション
複数のデータを同時に操作する場合に使用する
１つのオールオアナッシングの「TransactWriteItems」や「TramsactGetItems」オペレーションとして送信可
## SDKforJAVAのアプリで古いデータを上書き防止する
オブジェクト永続性モデルを使用した「バージョン番号にオプティミスティックロック」を使用する
オプティミスティックロックを有効にするためにDynamoDBVersionタグを使用できる
## 最近の変更を追跡・保存するリアルタイムデータを対象に分析する方法
DynamoDBストリームを有効にし、StreamViewTypeの値をNEW_IMAGEに設定
分析アプリ側でKinesisアダプターを使用してDynamoDBからのストリームを消費する
### DynamoStreams
KinesisDataStreamsAPIと類似
ListStreams、DescribeStreams、GetShards、GetShardItemratorの各オペレーションがある
### StreamViewTypeの有効な値
KEYS_ONLY：変更されたアイテムのキー属性のみがストリームに書き込まれる
NEY_IMAGE：アイテムが更新された後に表示される様になり、アイテム全体がストリームに書き込まれる
OLD_IMAGE：変更される前のアイテム全体がストリームに書き込まれる
NEW_AND_OLD_IMAGES：アイテムの新しいのと古いアイテム画像の両方がストリームに書き込まれる
### 1つずつ処理しているデータ処理で、ネットワーオーバーヘッドによりアプリのパフォーマンスが低下
バッチオペレーションは項目を並列で読み書きします。
1つずつ処理していたデータをまとめて実行できる処理としてリファクタリング
BatchGetItem：1つ以上のテーブルから最大100個の項目を読み取り
BatchWriteItem：1つ以上のテーブルから最大25個の項目を作成または削除
## 特定のパーティションに大容量に読み書きトラフィックが送信されている問題を解決
エラーの再執行と指数バックオフ(ExponentialBackoff)を実装
※指数関数的に処理のリトライ間隔を後退させるアルゴリズム
I/Oリクエストを均等に分散するリファクタリング
## GSIとLSIのスロットルについて
LSIはベーステーブルのキャパシティを使用するが、GSIは独自のキャパシティを使用して消費していく
GSIはベーステーブル以上のユニットをプロビジョニングする必要がある
## リクエスト
Scan: 全てのデータを取得
Query: 特定のデータを取得
## オペレーション(Put,Update,DaleteItem)のReturnCousumedCapacityパラメータ
TOTAL: 消費された書き込みキャパシティーユニットの総数
INDEXES: 消費された書き込みキャパシティユニットの総数とテーブル、オペレーションに影響うけたセカンダリインデックスの小計を返す
NONE: 書き込みキャパシティーの詳細(デフォルト)





# CloudFormation
## (EC2AMIIDの)パラメータ値を入力してテンプレートを再利用したい
Fn::Ref
## 依存してリソースをプロビジョニングしているサービス
ElasticBeanstalk
StepFunctions
## セクション
### Parameters
条件を評価する入力を定義(true or false)
条件で擬似パラメータを評価する場合、このセクションで擬似パラメータを定義する必要なし
## Conditions
組み込み関数を使用して条件を定義
リソースをいつ作成するか指定
## Resoueces and Ourputs
条件付きで作成するリソースまたは出力と条件を関連づける(trueはエンティティを作成し、falseは無視)
Conditionキーと条件の論理IDを使用してリソースや入力と関連づける
条件付きでプロパティを指定するにはfn::If関数を使用する
## ヘルパースクリプト(Python形式)
cfn-init: リソースメタデータの取得と解釈、パッケージのインストール、ファイルの作成、サービスの開始で使用する
cfn-init: CreaationPolicyまたはWaitConditionでシグナル送信するために使用、準備が整った時に他のリソースを同期
cfn-get-metadata: 特定のキーへのリソースまたはパスのメタデータを取得
cfn-hup: メタデータへの更新を確認し、変更が検出されたときにカスタムフックを実行
## ZipFileパラメーター
Node.js or Python関数のみテンプレートにインラインで関数コードを指定可能
これにより、関数ソースをインラインで含めるとAWSCloudFotmationはindexという名前のファイルに配置しzip化して展開パッケージを作成
## CloudFormationでLambdaをアップロードや更新する時に設定するパラメータ
依存関係がない場合はCloudFormationのAWS::Lambda::FunctionにLambda関数コードをインラインで記述する
Lambda関数コードをコードレポジトリーに保存してS3にアップロードしCloudFormationのAWS::Lambda::Functionにおいて参照する
## CloudFormationのスタックセット
異なるアカウントのテンプレートを一括管理して更新する場合に役立つ
複数のAWSアカウントやリージョンを横断したリソース展開が可能
## Lambda@Edge
CloudFormationの機能で、パフォーマンスが向上し、待ち時間が短縮される
アプリのユーザーに近いロケーションでコードが実行
## 組み込み関数
(Fn::ImportValue)別のスタックによってエクスポートされた出力値を返す。クロススタック参照を作成する際に利用される
(Fn::FindInMap)定義Fn::FindInMap: [ MapName, TopLevelKey, SecondLevelKey ]
## ユーザー認証プロセス待ち時間は最小限で特定のユーザーのみ私用できる目的で、不正アクセスは拒否したい
Lambda@EdgeとCognitoで実現可能
## Lambda関数とCloudformationテンプレートをAWSにアップロードしたい
aws cloudformation packageコマンド: テンプレートが参照するローカルアーティファクトをパッケージ化する。アーティファクトをS3にアップロードする
aws cloudformation deployコマンド: パッケージ化した後、deployコマンドでテンプレートをデプロイ
## 展開宙にトラフィックをシフトする3つの方法
Canary: 更新されたバージョンにシフトする割合と次の感覚を分単位で指定(CodeDeployDefault.LambdaCanary10Percent5Minutes)
Linear: 
All-at-once:



# Kinesis
## DataStreams
### スケールの方法
シャードを追加
パーティションキーに多様な異なる値が必要になる
## ProvisionedThroughputExceededExceptionエラーの対処方法
原因: 大量のデータを処理できていない
バッチメッセージの利用: 要求頻度またはサイズを減らして実行
エクスポネンシャルバックオフの実施: アルゴリズムのことをさし、エラー時に再施行間の待機時間を累進的に長くする


# Code
## Star
CI/CD環境のワンストップダッシュボードが作成される
## Pipeline
### ElasticBeanstalk環境と連携できず実行エラー発生した時のトラシュする方法
CloudFormationで原因探索
IAM Policy Simulatorで原因探索
CloudTrailで原因探索
## Build
### トラブルシューティング
CloudTrail
S3とCloudWatchの統合を有効にする
### デプロイのパフォーマンス改善
依存関係の解決の時間を解決するには最後の段階でソースコードの依存関係もバンドルし、コードと依存関係の両方を持たせる
### CodeBuildタイムアウト有効化
デフォルト60分、CLIから「queuedTImeoutInMinutesOverrride」を設定することで5分~480分まで任意に設定可能
## Commit
### コードなどの変更に反応するルールを統合で利用するサービス
CloudWatchイベント
### アクセスの仕方
HTTPS Git認証情報を設定する
新しいSSHキーを生成し、公開SSHキーを開発者の各IAMユーザーに関連づける
## Deploy
### デプロイ中に失敗してロールバックする時に利用されるデプロイID
新しいデプロイID
### ライフサイクルイベント(Hooksという機能)
BeforeAllowTraffic: デプロイされたLambda関数のバージョンに移行する前にタスクを実行する
AfterAllowTraffic: ~移行する後にタスクを実行する
ValidateService: デプロイが完了したことを確認するために使用する
BeforeInstall: インストールする前にタスクを実行する
### eb deploy
アプリをzip(WAR)ファイルとしてパッケージ化し、コマンドを実行することで新しいバージョンを実行できるようになる
### デプロイメントグループ
デプロイ中に私用する設定と構成が含まれている、
### ライフサイクルイベントの正しい順序
ApplicationStop
DownloadBundle
BeforeInstall
Afterinstall
ApplicationDtart
ValidateServece
### 失敗する可能性があり、問題をすばやくトラシュする場合の最適な展開設定
Buildをローカルで実行
# commit
## 暗号化について
リポジトリのデータは転送中及び保管中に自動的に暗号化される


# ALB
## アプリがクライアントのIPを取得するために必要な設定
X-Forwarded-For(リクエスト)ヘッダー

# IAM
## IAM Policy Simulator
IAMポリシー(適用前の)のテストし、トラブルシューティングする方法
## MFA認証を必要とするAPI操作をプログラムで呼び出す仕組みを実装する
GetSessionTokenAPI
## ACMが利用できない場合、SSL/TLS証明書を安全にインポートするサービス
IAMはプライベートキーを安全に暗号化し、暗号化されたバージョンをIAM SSL証明書ストレージに保存する
## アクセスキーの認証ファイル
Linux: ~/.aws/credentials
Windows: C:\Users\USER_NAME\.aws\credentials
## CLIからIAMの設定を確認する方法
--dry-run
応答エラー：DryRunOperation(それ以外はUnauthorizedOperation)

# SQS
## FIFO(First IN,First OUT)
順序の担保
## 可視生タイムアウト(Visibility Timeout)
設定時間内、他のコンシューマーによる同じメッセージの受信が0~30秒で防止される
## メッセージに重複したメッセージをSQSが送信しないようにするメッセージパラメータ
メッセージ重複排除ID
## 遅延キュー
0秒〜15分までのメッセージの配信を遅延することができる
## SQSキューで指定されたメッセージを削除
PurgeQueueアクション(削除まで最大60秒必要)
## キューに保存できるメッセージ最大数
無制限
## メッセージグループID
FIFOキューの順序を保守するためにClient_idに設定するメッセージパラメータ
## 古いデータを読み取るリスクを最小限に抑えるために10秒の遅延を設定したい
DelaySecondsパラメータを設定
## 一度に操作(送信、受信、削除)できるメッセージ数
10通
## 重複したメッセージを受信する際、ChangeMessageVisibility APIをコンシューマレベルで使用
可視性時間をコンシューマーの処理状況に基づいて動的に延長する設定が可能になる

# KMS
## S3にKMSを使用してアップロードすると「AccessDenied」になるエラーの対処法
ポリシーで「kms：Encrypt」「kms：Decrypt」権限を設定
AWS CLIによるマルチパートアップロードを実行
## エンベロープ暗号化を使用して大量のデータを暗号化する方法のために使用するAPIアクション
GenerateDataKey：ローカルでデータを暗号化するためにアプリで使用できる暗号化キーを返す
エンベロープ暗号化：データキーでプテーンテキストを暗号化したら、別のキーでデータキーを暗号化する
### 流れ
KMSコンソールでマスターキーを生成
マスターキーからデータキーを生成
データキーを使って平文データを暗号化
データキーを暗号化
暗号済みのデータキーと暗号亜k済みのデータを大切に保管
## 最大データサイズは4KB
パスワードやRSAキーなどの少量データの暗号化に適しているが、アプリのデータ暗号には不向き


# AWS AppSync
## CognitoSyncとAppSync
同じ様に利用されるがCognitoよりAppSyncの方が新しく、使用するこを水晶されている

# S3
## CLIで大きな項目リストを返す場合(デフォルト1000ページサイズ)のCLIのオプション
(aws s3api list-objects)--max-items: 一度に含める項目を少なくすることが可能
(aws s3api list-objects)--page-size: サービスの1回の呼び出しで要求する項目数を少なくすることが可能
## SSE-Cを使用しているバケットにデータをアップロードする際リクエストにヘッダーを含める設定をする方法
x-amz-server-side-encription-customer-key-MD5: RFC1321にしたがってbase64の128ビットMD5ダイジェストを指定できる
x-amz-server-side-encryption-customer-key: 複合する際にbase64でエンコードされた256ビットの暗号キーを指定できる
x-amz-server-side-encription-customer-algorithm: アルゴリズム指定、ヘッダーの値はAES265

# EBS
## 既存インスタンスにEBSをアタッチ後にボリュームを使用するために必要な設定
ボリュームにファイルシステムを作成

# AWS Cognito
## IDプールとユーザープールの用途
### IDプール
S3バケットやDynamoDBテーブルなどのAWSリソースへのあくせすをユーザーに許可
未承認ユーザー用のAWS認証情報を一時的に生成
### ユーザープール
アプリのサインアップとサインインウェブページを設計
ユーザーデータにアクセスし管理
ユーザーのデバイス、場所、IPアドレスを追跡し、リクエストレベルのサインイン要求に適応
アプリのカスタム認証フローを使用する
## SAML2.0によるエンタープライズIDプロバイダーを使用してサインインしたい
IDフェデレーションとCognitoの統合を有効化
AWS Single Sign-ONによりOrganizationsの全てのアカウントへのSSOアクセスとユーザーアクセス権限を一元管理

# STS
## メッセージをデコードされるように設定変更をする実装方法
AWS STS decode-authorization-massegeを私用してデコード処理を実装

# ElasticCache
## キャッシュ戦略
遅延読み込み: 必要なときにキャッシュを読み込む
書き込みスルー: 書き込みの際はデータベースの更新と共に常にキャッシュも更新して最新化する
## MemcachedとRedisの比較
Memcached: 需要の増減に応じてノードを追加・削除するスケールイン・アウト機能がある
Redis: マルチスレッドアーキテクチャをサポートしてない。プロトタイプ分散システムにて耐久性を提供できる

# RDS
## ストレージに書き込まれる前に暗号化した
透過的なデータ暗号化(TDE)

# 暗号化
## KMSのAPIがリクエスト上限を迎えた場合の暗号化対処
AWS暗号化SDKを使用する

# CloudWatch
## RDSの毎月バックアップを3ヶ月保持したい(RDSのバックアップでは不可能)
ClouddWatchでcronイベントを作成し、スナップショット機能をトリガーにするLambdaを利用
※RDSのバックアップ保持期間は0~35日
## Logs
### 最大メモリ使用によるエラーが表示された場合の対処
CloudWatchlogの有効期限ポリシーを設定する
デフォルトでは、ログは無期限に保持され、有効期限はありません。そのため、ログが無制限に蓄積させてしまい、最大メモリ使用による関するエラーが発生

# Route53
## レコード
Aレコード: ドメイン、サブドメインをIPアドレスに向ける
AAAAレコード: ホスト名に対するIPv6アドレスを定義
CNAMEレコード: 別名に対する正式名を指定する
エイリアスレコード: AWSリソースにトラフィックをルーティング可能

# AWS SAM
CloudFormationの拡張機能
## API
AWS::Serverless::{API name}

# CLI
## 作成するリージョンを変更
--region

# SecretsManager
## データベースの認証情報
ライフサイクルを通して容易にローテーション、管理、取得できる
