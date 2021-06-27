# AWS認定ソリューションアーキテクトアソシエイト対策

## 目次

<!-- TOC -->

- [AWS認定ソリューションアーキテクトアソシエイト対策](#aws認定ソリューションアーキテクトアソシエイト対策)
    - [目次](#目次)
    - [グローバグインフラストラクチャとネットワーク](#グローバグインフラストラクチャとネットワーク)
        - [リージョンとアベイラビリティゾーン（AZ）](#リージョンとアベイラビリティゾーンaz)
            - [VPC (Amazon Virtual Private Cloud](#vpc-amazon-virtual-private-cloud)
    - [ネットワーキングとコンテンツ配信](#ネットワーキングとコンテンツ配信)
        - [CloudFront](#cloudfront)
        - [Route53](#route53)
        - [Global Accelerator](#global-accelerator)
    - [コンピューティングサービス](#コンピューティングサービス)
        - [EC2](#ec2)
            - [インスタンスタイプ](#インスタンスタイプ)
            - [スポットインスタンス](#スポットインスタンス)
        - [ELB](#elb)
        - [ECS](#ecs)
        - [EKS](#eks)
        - [AWS Fargate](#aws-fargate)
        - [Lambda](#lambda)
    - [運用支援サービス（モニタリング）](#運用支援サービスモニタリング)
        - [CloudWatch](#cloudwatch)
        - [CloudTail](#cloudtail)
        - [Amazon Inspector](#amazon-inspector)
        - [Trusted Advisor](#trusted-advisor)
    - [ストレージサービス](#ストレージサービス)
        - [EBS](#ebs)
        - [EFS](#efs)
        - [S3](#s3)
            - [標準](#標準)
            - [Intelligent-Tiering](#intelligent-tiering)
            - [低頻度アクセス（標準 - AI)](#低頻度アクセス標準---ai)
            - [1 ゾーン・低頻度アクセス（1ゾーン - AI）](#1-ゾーン・低頻度アクセス1ゾーン---ai)
            - [Glacier](#glacier)
            - [Glacier Deep　Archive](#glacier-deep　archive)
        - [Storage Gateway](#storage-gateway)
        - [FSx](#fsx)
    - [データベースサービス](#データベースサービス)
        - [RDS](#rds)
        - [Redshift](#redshift)
        - [dynamoDB](#dynamodb)
        - [ElastiCahce](#elasticahce)
        - [その他](#その他)
    - [セキュリティとアイデンティティ](#セキュリティとアイデンティティ)
        - [IAM](#iam)
        - [Artifact](#artifact)
        - [カスタマーコンプライアンスセンター](#カスタマーコンプライアンスセンター)
        - [KMS / CloudHSM](#kms--cloudhsm)
        - [AWS Certificate Manager](#aws-certificate-manager)
    - [アプリケーションサービス](#アプリケーションサービス)
        - [SQS](#sqs)
        - [SWF / Step Function](#swf--step-function)
        - [SNS(Simple Notification Service)](#snssimple-notification-service)
        - [SES](#ses)
    - [開発者ツール](#開発者ツール)
        - [CodeCommit](#codecommit)
        - [CodeBuild](#codebuild)
        - [CodeDeploy](#codedeploy)
        - [CodePipeline](#codepipeline)
    - [プロビジョニングサービス](#プロビジョニングサービス)
        - [Elastic Beanstalk](#elastic-beanstalk)
        - [OpsWorks](#opsworks)
        - [CloudFormation](#cloudformation)
    - [分析サービス](#分析サービス)
        - [★EMR](#★emr)
        - [ELT](#elt)
        - [その他](#その他)
    - [管理サービス](#管理サービス)
        - [コンシェルジュ](#コンシェルジュ)
        - [プロフェッショナルサービス](#プロフェッショナルサービス)
        - [Config](#config)
        - [System Manager](#system-manager)
    - [料金](#料金)
        - [AWS料金計算ツール](#aws料金計算ツール)
        - [請求ダッシュボード](#請求ダッシュボード)
            - [Budgets](#budgets)
            - [Cost Exproler](#cost-exproler)
    - [サポート](#サポート)
        - [ベーシックサポート](#ベーシックサポート)
        - [デベロッパーサポート](#デベロッパーサポート)
        - [ビジネスサポート](#ビジネスサポート)
        - [エンタープライズサポートプラン](#エンタープライズサポートプラン)
    - [アーキテクチャ設計](#アーキテクチャ設計)
    - [共通用語](#共通用語)

<!-- /TOC -->


* 試験ガイド  
https://d1.awsstatic.com/ja_JP/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf

* AWSサービス別資料  
https://aws.amazon.com/jp/aws-jp-introduction/aws-jp-webinar-service-cut/


## グローバグインフラストラクチャとネットワーク


### リージョンとアベイラビリティゾーン（AZ）
  
#### VPC (Amazon Virtual Private Cloud

* インターネットゲートウェイ(IGW)
* 仮想プライベートゲートウェイ(PGW)
* マルチAZ  
同一の役割を持ったサブネットを複数のAZにそれぞれ作成する。

* パブリックサブネット  
ルーティングで直接接続しているサブネット。  
グローバルIPを設定したEC2等やNATゲートウェイを配置する。

* プライベートサブネット  
ルーティングが直接インターネットに接続していないサブネット。

* NATゲートウェイ  
グローバルIPを持つ。プライベートIPをNATゲートウェイが持つグローバルIPに変換して外部と通信する。

* セキュリティグループ(SG)  
ファイアウォール相当。  
ステートフルなので、レスポンスを考慮しなくてもよい。  
ネットワークACLの次に評価される。

* ネットワークACL(Access Control List)  
タイプ・プロトコル・ポート・IP・送受信でアクセスを制御（許可/拒否）を設定する。
ステートレスなので、レスポンスも明示的に指定する必要あり。  
サブネット単位に有効。

* VPCエンドポイント
  * ゲートウェイポイント  
    S3やDynamoDBなどのAWSサービスと接続するゲートウェイエンドポイント。
  * AWS PrivateLink
    トラフィックをパブリックインターネットをに公開せずVPC・AWSサービス・オンプレと接続するサービス。

* VPCピアリング
  2つのVPCをプライベートに接続する機能。

* VPCフローログ
  ENI(AWSの仮想NIC。Elastic Network Interface,ENI)単位に記録されるネットワークログ。

* Direct Connect
  AWSとデータセンターと専用線で接続する。

* Direct Connect Gateway
  Direct Connect経由で別のAWSアカウントのVPC

* AWS Transit Gateway
  複数のVPCとオンプレを中央ハブを介して接続するサービス。

## ネットワーキングとコンテンツ配信

### CloudFront

https://d1.awsstatic.com/webinars/jp/pdf/services/20190730_AWS-BlackBelt_Amazon_CloudFront.pdf  
https://www.youtube.com/watch?v=mmRKzzOvJJY

課金対象  
* AWSからのデータ転送アウト
* ユーザからのリクエストの数と種類、リクエストが行われた地域
* トラフィック分散

### Route53

* 位置情報ルーティングポリシー  
ユーザの位置情報に基づいてルーティングする。  
日本からのアクセスは日本語コンテンツが配置されたWebサーバーに接続するという制御が可能。

### Global Accelerator

地理的に近いエンドポイントにTCP/UDPトラフィックを最適にルーティングする。

## コンピューティングサービス

### EC2

#### インスタンスタイプ

* オンデマンド  
使った分だけ。

* Savings Plans  
一定のコンピューティング使用料を1年または3年の期間で契約する。  
契約した使用料を超えた分はオンデマンド料金。

* リザーブドインスタンス
  * 利用期間は1年 or 3年。
  * 前払いで割引価格で購入可能。
  * 利用しなくなったらマーケットプレイスで販売可能。
  * コンパーチブルタイプでは属性を変更可能。

* Dedicated Hosts  
専用サーバ。最も高価なオプション。

#### スポットインスタンス
キャパシティの空き具合によって最大90％の割引。  
空きがなくなると中断される可能性がある。


### ELB

### ECS

### EKS

Elastic Kubernetes Service

### AWS Fargate

ESC,EKS(Elastic Kubernetes Service)で動作するコンテナ向けサーバレスコンピューティングエンジン。

### Lambda

## 運用支援サービス（モニタリング）

### CloudWatch

### CloudTail

### Amazon Inspector

自動的にアプリケーションに対し、露出・脆弱性・ベストプラクティスからの逸脱がないかどうか確認できる。

### Trusted Advisor

AWSのベストプラクティスに基づいてリソースに対しリアルタイムに推奨事項を提供するサービス。
* コスト最適化
* パフォーマンス
* セキュリティー
* フォールトトレランス（耐障害性）
* サービス制限

## ストレージサービス

### EBS

* インスタンスストア  
スループットが早い。揮発性でEC2を終了するとデータが消える。

### EFS

NFSv4(Network File System)プロトコルによるデータ転送をサポートしている。

### S3

以下のストレージクラスがある。
#### 標準
#### Intelligent-Tiering
アクセスパターンに応じて自動的にコストを削減する。
頻繁・低頻度・アーカイブ・ディープアーカイブの4層をもち、アクセスパターンによって、自動的にデータを移動する。

#### 低頻度アクセス（標準 - AI)
格納コストが安価で、頻繁にアクセスしないが高速なアクセスが必要な場合に使う。

#### 1ゾーン・低頻度アクセス（1ゾーン - AI）
1AZにデータを保存。可用性が低くなるが低コスト。

#### Glacier
低コストで長期保存。
データ取り出しには事前にリクエストが必要で、取り出し可能になるまで数分〜数時間かかる。

#### Glacier Deep　Archive
一年に1・2回しかアクセスしないデータの保存用。
取り出し可能になるまで、最大12h。

### Storage Gateway

https://d1.awsstatic.com/webinars/jp/pdf/services/20170125_AWS-BlackBelt-StorageGateway_20170223Update.pdf

オンプレミスにあるデータをクラウドへ連携するためのインターフェイス。  
S3、S3Glacier、EBSなどを利用する。

* S3ファイルゲートウェイ  
  S3をバックエンドストレージとして使用。  
  NFSでバケットを共有。ファイルをS3のバケットとして保管。

* FSxファイルゲートウェイ  
  Amazon FSxに保管。

* ボリュームゲートウェイ  
  ディスクデータをスナップショットとしてS3に取得。  
  iSCSIでブロックストレージとしてインターフェイスを提供。

  * Gateway-Stored Volumes  
    データのプライマリコピーはローカル。

  * Gateway-Cashed Volumes  
    ローカルにキャッシュストレージを持ち、アクセス頻度の高いデータを保管。

* テープゲートウェイ


### FSx

## データベースサービス

### RDS

* マルチAZ配置  
  目的は、高可用性。
  自動フェイルオーバーを実現。

* マルチリージョン配置  
  目的は、災害復旧

* リードレプリカ  
  目的は、スケーラビリティ。

### Redshift

データウェアハウス向けデータベース

* ホワイトペーパー  
https://d1.awsstatic.com/whitepapers/amazon-redshift-cost-optimization.pdf?did=wp_card&trk=wp_card

* Black Belt  
https://www.youtube.com/watch?v=Myzy68VEXjM  
https://d1.awsstatic.com/webinars/jp/pdf/services/20200318_AWS_BlackBelt_Redshift.pdf

Redshiftクラスタ  
複数ノードによる分散並列実行

* リーダーノード  

  各クラスタに1台のみ。
  SQLをクライアントから受け付ける。  
  SQLをコンパイルし、コンピュートノードに配信する。  
  コンピュータノードの処理結果をクライアントに返す。

* コンピュートノード  
  クエリを並列実行する。  
  データをローカルキャッシュ or S3から取り出してクエリを処理する。  
  処理結果をリーダーノードに返す。

* スライスノード  
  分散処理する最小単位。コンピュートノードに存在。
  
* データはS3かローカルキャッシュSSD

* 列指向ストレージ
  行指向（RDB）に対し、列だけスキャンするので不必要なIOを低減。

* データ圧縮  
  データに合わせて圧縮率の高い圧縮方法が採用される。

* ゾーンマップ
  ブロック単位を1MBと大きくとってディスクIOを効率化。  
  ゾーンマップはブロックの最小・最大値を管理するメタデータ。リーダーノードのメインメモリに格納。不必要なブロックを読み飛ばす。

* ソートキー  
  データをどの列順にソートするかを、テーブルごとに指定したもの。  
  頻繁に使用される絞り込み（ID、日付が多い）条件が筆頭。

* データ分散

* マテリアライズドビュー  
  よく利用する結合をあらかじめ計算しておく。
  
* Redshift Spectrum  
  S3を直接参照できるサービス。

* スナップショット  
  クラスタごとに8時間ごと、5Gデータ増加時に自動的に作成される。

### dynamoDB

### ElastiCahce

### その他

## セキュリティとアイデンティティ

### IAM

* 最小権限の原則  
ユーザに必要なアクセス権限のみ与える。

* Security Token Service(STS)  
AWSのサービスにアクセスできる一時的な限定権限認証情報を取得できる。

* ルートユーザ

* ユーザ

* グループ

* ポリシー  
APIコールに対しての許可／拒否の定義。JSONで記載。  
APIコールを実行するAWSリソース。
ユーザ・グループにアタッチ。

* ロール
一時的なアクセス許可の利用。  
  * 
  * AWSリソース。
  * 外部のアイデンティティ
  * アプリケーション
  * AWSの他のサービス。

### Artifact
セキュリティおよびコンプライアンスレポートのオンデマンドでの利用と、特定のオンライン契約を提供するサービス。

* Artifact Agreements
  AWSを使用することに関して会社がAWSの契約に署名する必要がある場合に利用。  
  個別アカウントとOrganizationsのすべてのアカウントに置いて契約の確認、受諾、管理を行うことができる。

* Artifact Reports
  サードパーティの監査人からのコンプライアンスレポートを提供する。
  これにより、監査人または規制機関にAWSのセキュリティ制御の証拠を提示できる。

### カスタマーコンプライアンスセンター
AWSコンプライアンスの詳細を確認するために役立つリソース。
規制対象の業界の企業がコンプライアンス、ガバナンス、監査に関する課題をどの様に解決したか知ることができる。

* コンプライアンスに関する重要な質問に対するAWSの回答
* AWSリスクとコンプライアンスの概要
* セキュリティ監査チェックリスト

監査人向けのラーニングパスもある。

### KMS / CloudHSM

### AWS Certificate Manager

## アプリケーションサービス

### SQS
コンポーネント間でメッセージを送信、保存、受信できる。
疎結合されたアプリケーションとマイクロサービスの実現に必要。

### SWF / Step Function

### SNS(Simple Notification Service)
パブリッシャーがサブスクライバーにメッセージを発行できる。  
サブスクライバーはwebサーバー、Eメールアドレス、Lamdba関数など。

### SES

## 開発者ツール

### CodeCommit

### CodeBuild

### CodeDeploy

### CodePipeline

## プロビジョニングサービス

### Elastic Beanstalk

アプリケーションを素早くデプロイし管理を自動化できる。  
Git・IDEからアプリケーションをアップロードするだけで、デプロイの詳細（容量プロビジョニング、負荷分散、AutoScaling、アプリケーションのヘルスモニタリングなど）を処理する。

### OpsWorks

ChefやPuppetのコードを使ってインフラ構成の自動化、構成管理を行う。

### CloudFormation

コードに基づいてクラウドインフラを構築することができる。  
アプリケーション展開は直接は不可。

## 分析サービス

### ★EMR

### ELT

### その他

## 管理サービス

### コンシェルジュ

エンタープライズサポートプラン。

### プロフェッショナルサービス

### Config

リソースの設定を評価、監査、審査できるサービス。
リソースのプロビジョンニング・設定のルールを定義でき、逸脱がないかチェックできる。

### System Manager

AWSサービスのデータを一元管理し、構成を可視化する。  
運用タスクを自動化する。

## 料金

### AWS料金計算ツール
ユースケースのコスト見積もりを作成できる。

### 請求ダッシュボード

#### Budgets
予算を作成してサービスの使用料・コスト・インスタンスの予約を計画できる。  
予算を超えた場合に通知するカスタムアラートを設定できる。

#### Cost Exproler
時間の経過に伴うｓコストと使用状況を表示・分析するツール。


## サポート

### ベーシックサポート
無料。  
ホワイトメーパー、ドキュメント、サポートコミュニティを利用できる。

### デベロッパーサポート
* ベストプラクティスのガイダンス
* クライアント側の診断ツール
* 基盤となるアーキテクチャのサポート。製品、機能サービスの使用方法をガイダンス。  
サービスや機能の組み合わせを特定するのに役立つ。

### ビジネスサポート
* 特定のニーズを適切にサポートできるAWS製品・機能・サービスを特定するためのユースケースガイダンス。
* Trusted Advisorの全てのチェック。
* 一般的なOS、アプリケーションなど、サードパーティソフトウェアの限定的サポート。

### エンタープライズサポートプラン

* 特定のユースケースとアプリケーションを支援するコンサルティング。
* Infractructure Event Management  
AWSエキスパートがイベント計画に関わり、アーキテクチャやスケーリング、運用に関するガイダンスやアプローチを提供する。
* テクニカルアカウントマネージャー（TAM）  
アプリケーションの計画、デプロイ、最適化に関するガイダンスやレビューを提供する。  
ユーザと継続的に連絡をとる。

## アーキテクチャ設計


## 共通用語

* 単一障害点  
Single Point Of Failure(SPOF)