# AWS認定ソリューションアーキテクトアソシエイト対策

## 目次

<!-- TOC -->

- [AWS認定ソリューションアーキテクトアソシエイト対策](#aws認定ソリューションアーキテクトアソシエイト対策)
    - [目次](#目次)
    - [AWS Well-Architected](#aws-well-architected)
        - [運用上の優秀性（Operational Exellence）](#運用上の優秀性operational-exellence)
        - [セキュリティ（Security）](#セキュリティsecurity)
            - [責任共有モデル](#責任共有モデル)
        - [信頼性（Reliability）](#信頼性reliability)
        - [パフォーマンス効率（Performance Efficiency）](#パフォーマンス効率performance-efficiency)
        - [コスト最適化（Cost Optimization）](#コスト最適化cost-optimization)
    - [グローバルインフラストラクチャ](#グローバルインフラストラクチャ)
        - [リージョン](#リージョン)
        - [アベイラビリティーゾーン（AZ）](#アベイラビリティーゾーンaz)
    - [アナリティクス](#アナリティクス)
        - [Athena](#athena)
        - [Elasticsearch Service(AWS ES)](#elasticsearch-serviceaws-es)
        - [EMR](#emr)
        - [Glue](#glue)
        - [Kinesis](#kinesis)
            - [Data Firehose](#data-firehose)
            - [Data Stream](#data-stream)
            - [Data Analytics](#data-analytics)
            - [Agent](#agent)
        - [Quick Sight](#quick-sight)
    - [AWS の請求情報とコスト管理](#aws-の請求情報とコスト管理)
        - [AWS料金計算ツール（AWS Pricing Calculator）](#aws料金計算ツールaws-pricing-calculator)
        - [請求ダッシュボード](#請求ダッシュボード)
            - [Budgets](#budgets)
            - [Cost Exproler](#cost-exproler)
    - [アプリケーション統合](#アプリケーション統合)
        - [SNS(Simple Notification Service)](#snssimple-notification-service)
        - [SQS](#sqs)
    - [コンピューティング](#コンピューティング)
        - [EC2](#ec2)
            - [インスタンス購入オプション](#インスタンス購入オプション)
            - [スポットインスタンス](#スポットインスタンス)
            - [ブートストラップ](#ブートストラップ)
            - [ゴールデンイメージ](#ゴールデンイメージ)
        - [Elastic Beanstalk](#elastic-beanstalk)
        - [ECS](#ecs)
        - [EKS](#eks)
        - [AWS Fargate](#aws-fargate)
        - [ELB](#elb)
        - [Lambda](#lambda)
    - [データベースサービス](#データベースサービス)
        - [RDS](#rds)
            - [ストレージ](#ストレージ)
        - [Redshift](#redshift)
        - [dynamoDB](#dynamodb)
            - [読み込み整合性](#読み込み整合性)
            - [料金](#料金)
        - [Aurora](#aurora)
        - [ElastiCahce](#elasticahce)
            - [Memcashed](#memcashed)
            - [Redis](#redis)
    - [マネジメント、ガバナンス](#マネジメントガバナンス)
        - [AWS Auto Scaling](#aws-auto-scaling)
        - [AWS Backup](#aws-backup)
        - [OpsWorks](#opsworks)
        - [CloudFormation](#cloudformation)
        - [AWS CloudTrail](#aws-cloudtrail)
        - [CloudWatch](#cloudwatch)
            - [CloudWatch Logs](#cloudwatch-logs)
            - [CloudWatch Events](#cloudwatch-events)
        - [Config](#config)
        - [EventBridge（CloudWatch Events)](#eventbridgecloudwatch-events)
        - [AWS Organizations](#aws-organizations)
        - [AWS Resource Access Manager](#aws-resource-access-manager)
        - [AWS Systems Manager](#aws-systems-manager)
        - [Trusted Advisor](#trusted-advisor)
    - [移行、転送](#移行転送)
        - [AWS Database Migration Service (AWS DMS)](#aws-database-migration-service-aws-dms)
        - [AWS DataSync](#aws-datasync)
        - [AWS Migration Hub](#aws-migration-hub)
        - [AWS Server Migration Service (SMS)](#aws-server-migration-service-sms)
        - [AWS Snowball](#aws-snowball)
        - [AWS Transfer Family](#aws-transfer-family)
    - [ネットワーク、コンテンツ配信](#ネットワークコンテンツ配信)
        - [Amazon API Gateway](#amazon-api-gateway)
        - [CloudFront](#cloudfront)
        - [AWS Direct Connect](#aws-direct-connect)
        - [Global Accelerator](#global-accelerator)
        - [Route53](#route53)
            - [Resolver](#resolver)
            - [Resolver for Hybrid Clouds](#resolver-for-hybrid-clouds)
            - [トラフィックフロー](#トラフィックフロー)
        - [AWS Transit Gateway](#aws-transit-gateway)
        - [VPC (Amazon Virtual Private Cloud）](#vpc-amazon-virtual-private-cloud)
            - [インターネットゲートウェイ(IGW)](#インターネットゲートウェイigw)
            - [仮想プライベートゲートウェイ(PGW)](#仮想プライベートゲートウェイpgw)
            - [マルチAZ](#マルチaz)
            - [パブリックサブネット](#パブリックサブネット)
            - [プライベートサブネット](#プライベートサブネット)
            - [NATゲートウェイ](#natゲートウェイ)
            - [セキュリティグループ(SG)](#セキュリティグループsg)
            - [ネットワークACL(Access Control List)](#ネットワークaclaccess-control-list)
            - [VPCエンドポイント](#vpcエンドポイント)
            - [VPC Peering](#vpc-peering)
            - [VPCフローログ](#vpcフローログ)
            - [NLB](#nlb)
            - [Site-to-Site VPN(サイト間VPN)](#site-to-site-vpnサイト間vpn)
    - [セキュリティ、アイデンティティ、コンプライアンス](#セキュリティアイデンティティコンプライアンス)
        - [AWS Certificate Manager](#aws-certificate-manager)
        - [AWS Directory Service](#aws-directory-service)
            - [AD Connector](#ad-connector)
        - [Amazon GuardDuty](#amazon-guardduty)
        - [IAM](#iam)
        - [Amazon Inspector](#amazon-inspector)
        - [AWS Key Management Service(KMS)](#aws-key-management-servicekms)
            - [カスタマーキー（CMK）](#カスタマーキーcmk)
        - [Amazon Macie](#amazon-macie)
        - [AWS Secrets Manager](#aws-secrets-manager)
        - [AWS Shield](#aws-shield)
        - [AWS Single Sign-On](#aws-single-sign-on)
        - [AWS WAF](#aws-waf)
    - [ストレージ](#ストレージ)
        - [EBS](#ebs)
        - [EFS](#efs)
        - [FSx](#fsx)
        - [S3](#s3)
            - [ストレージクラス](#ストレージクラス)
        - [Storage Gateway](#storage-gateway)
    - [ソリューションアーキテクト範囲外？](#ソリューションアーキテクト範囲外)
        - [Artifact](#artifact)
        - [カスタマーコンプライアンスセンター](#カスタマーコンプライアンスセンター)
        - [SWF / Step Function](#swf--step-function)
        - [SES](#ses)
        - [CodeCommit](#codecommit)
        - [CodeBuild](#codebuild)
        - [CodeDeploy](#codedeploy)
        - [CodePipeline](#codepipeline)
        - [コンシェルジュ](#コンシェルジュ)
        - [プロフェッショナルサービス](#プロフェッショナルサービス)
        - [サポート](#サポート)
            - [ベーシックサポート](#ベーシックサポート)
            - [デベロッパーサポート](#デベロッパーサポート)
            - [ビジネスサポート](#ビジネスサポート)
            - [エンタープライズサポートプラン](#エンタープライズサポートプラン)

<!-- /TOC -->


* 試験ガイド  
https://d1.awsstatic.com/ja_JP/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf

* AWSサービス別資料  
https://aws.amazon.com/jp/aws-jp-introduction/aws-jp-webinar-service-cut/


## AWS Well-Architected

https://aws.amazon.com/jp/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc

### 運用上の優秀性（Operational Exellence）

### セキュリティ（Security）

#### 責任共有モデル

https://aws.amazon.com/jp/compliance/shared-responsibility-model/

* ユーザがAWSから継承される統制  
  * 物理統制
  * 環境統制

  実施状況を継承して、コンプライアンスに対応できる。
  AWS Artifactからレポートを入手することで物理統制の評価が可能。

* 共有統制
  * パッチ管理
  * 構成管理
  * 意識とトレーニング

* ユーザ固有

  サービス・データ・通信の保護。  
  ゾーンセキュリティ。
  



### 信頼性（Reliability）

### パフォーマンス効率（Performance Efficiency）

### コスト最適化（Cost Optimization）


## グローバルインフラストラクチャ

### リージョン

### アベイラビリティーゾーン（AZ）

リージョン内のアベイラビリティーゾーンは低遅延リンクで接続されており、AZ間のデータ同期を低遅延で実現している。




## アナリティクス

### Athena

S3にあるデータを標準SQLをつかって簡単に分析できるクエリサービス。

クエリ単位に課金。S3データスキャン1TBに対し5USD。  
DDL、失敗クエリには課金されない。

### Elasticsearch Service(AWS ES)

全文検索サービス。

### EMR

分散処理フレームワークによるビックデータのクラウドプラットフォーム。

ユースケース  
* 機械学習
* ETL(Exact抽出、Transform加工、Load読み出し)
* クイックストリーム分析
* リアルタイムストリーミング分析
* ゲノミクス

分散フレームワーク  
* マスターノード：ノード間でのデータおよびタスク分散を調整する。
* コアノード：タスクを実行し、Hadoop Distributed File System（HDFS）にデータを保存。
* タスクノード：タスクのみ実行。データは持たない。

### Glue

### Kinesis

#### Data Firehose

蓄積前にデータを加工する。

#### Data Stream

ストリーム処理向けのアプリケーションを構築できる。

#### Data Analytics

ストリームデータのリアウタイム解析を行う。

#### Agent

ストリーミングデータを収集して取り込む仕組みをアプリケーションに実装できる。

### Quick Sight

## AWS の請求情報とコスト管理

### AWS料金計算ツール（AWS Pricing Calculator）
ユースケースのコスト見積もりを作成できる。

簡易コスト計算ツールは廃止された。


### 請求ダッシュボード

#### Budgets
予算を作成してサービスの使用料・コスト・インスタンスの予約を計画できる。  
予算を超えた場合に通知するカスタムアラートを設定できる。

#### Cost Exproler
時間の経過に伴うｓコストと使用状況を表示・分析するツール。

## アプリケーション統合

### SNS(Simple Notification Service)
パブリッシャー（プロデューサー）がサブスクライバー（コンシューマー）にメッセージを発行できる。  
サブスクライバーはwebサーバー、Eメールアドレス、Lamdba関数など。
非同期通信を実現する。


### SQS
コンポーネント間でメッセージを送信、保存、受信できる。
疎結合されたアプリケーションとマイクロサービスの実現に必要。


## コンピューティング

### EC2

#### インスタンス購入オプション

* オンデマンド  
使った分だけ。

* Savings Plans  
一定のコンピューティング使用料を1年または3年の期間で契約する。  
契約した使用料を超えた分はオンデマンド料金。

* リザーブドインスタンス
  * 利用期間は1年 or 3年。
  * スタンダードで前払いで割引価格で購入可能。ただし1ヶ月以上の期間が残っていること。
  * 利用しなくなったらマーケットプレイスで販売可能。
  * コンパーチブルタイプでは属性を変更可能。

* Dedicated Hosts  
専用サーバ。最も高価なオプション。

#### スポットインスタンス

キャパシティの空き具合によって最大90％の割引。  
空きがなくなると中断される可能性がある。

#### ブートストラップ

EC2起動時に自動ブートストラップスクリプトを実行し、ソフトウェアをインストールしたり、データコピーである特定の状態にしたりできる。

#### ゴールデンイメージ

そのリソースの最適な状態を保存したAMIやスナップショット。

### Elastic Beanstalk

アプリケーションを素早くデプロイし管理を自動化できる。  
Git・IDEからアプリケーションをアップロードするだけで、デプロイの詳細（容量プロビジョニング、負荷分散、AutoScaling、アプリケーションのヘルスモニタリングなど）を処理する。

### ECS

### EKS

Elastic Kubernetes Service

### AWS Fargate

ESC,EKS(Elastic Kubernetes Service)で動作するコンテナ向けサーバレスコンピューティングエンジン。

### ELB

### Lambda

* 課金要素は利用時間とリクエスト数。

## データベースサービス

### RDS

* マルチAZ配置  
  目的は、高可用性。
  自動フェイルオーバーを実現。  
  後からでもマルチAZ化可能。  
  フェイルオーバは手動も可能。

* マルチリージョン配置  
  目的は、災害復旧

* リードレプリカ  
  目的は、スケーラビリティ。  
  RDSは5台まで。

#### ストレージ

* 汎用SSD
* プロビジョンドIOPS
* マグネティック

### Redshift

データウェアハウス向けデータベース

* ホワイトペーパー  
https://d1.awsstatic.com/whitepapers/amazon-redshift-cost-optimization.pdf?did=wp_card&trk=wp_card

* Black Belt  
https://www.youtube.com/watch?v=Myzy68VEXjM  
https://d1.awsstatic.com/webinars/jp/pdf/services/20200318_AWS_BlackBelt_Redshift.pdf

大量データの保存や並列処理によるパフォーマンス向上が可能。

業務解析システム用のデータベースに最適。

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
  S3に保存されるのでコストがかかる。

### dynamoDB

* グローバルテーブル  
グローバルに展開されたアプリケーションに対して高速読み取りを提供するレプリケーションの仕組み。  
マルチリージョンにマルチマスターデータベースをデプロイする。  
グローバルなユーザに低レイテンシーアクセスを提供する。

* DAX  
インメモリキャッシュ。

#### 読み込み整合性

* 結果生合成のある読み込み  
最新の書き込み結果が反映されない場合がある。

* 強い生合成のある読み込み  
全ての書き込みが完了したデータを読み取る。  
GSIでは利用不可。

#### 料金

* 同じリージョンのAZ間のデータ転送は無料。
* リージョン間のデータ転送は、送受信リージョン双方に課金される。

### Aurora

マルチAZにまたがって仮想ボリュームが構成されている。


### ElastiCahce

完全マネージド型インメモリデータベース。  
高速リアルタイム処理、トランザクションが可能。  
KVS(Key-Valueストア)

#### Memcashed

* シンプルなキャッシュシステム
* データに永続性はない。
* バックアップと復元機能はない。
* スケールイン・スケールアウトが可能

#### Redis

* 多様なデータ型が利用できる
* 永続性がある
* フェイルオーバ・バックアップリストが可能
* pub/sub機能を提供。
* 全ての操作は排他的。
* シングルスレッドで動作。


## マネジメント、ガバナンス

### AWS Auto Scaling

### AWS Backup

### OpsWorks

ChefやPuppetのコードを使ってインフラ構成の自動化、構成管理を行う。

### CloudFormation

コードに基づいてクラウドインフラを構築することができる。  
アプリケーション展開は直接は不可。

### AWS CloudTrail

### CloudWatch

#### CloudWatch Logs

#### CloudWatch Events

### Config

リソースの設定を評価、監査、審査できるサービス。
リソースのプロビジョンニング・設定のルールを定義でき、逸脱がないかチェックできる。

### EventBridge（CloudWatch Events)

### AWS Organizations

* 複数のアカウントの管理
* 複数アカウントの一括請求
* ポリシーの集中管理
* 利用できるサービスの制限

### AWS Resource Access Manager

### AWS Systems Manager

AWSサービスのデータを一元管理し、構成を可視化する。  
運用タスクを自動化する。

* リソースグループごとに運用データを確認できる。
* 各リソースグループをタグごとに管理・仕分けることができる。
* EC2のパッチ、更新、設定変更、削除、停止、デプロイを自動化できる。

### Trusted Advisor

AWSのベストプラクティスに基づいてリソースに対しリアルタイムに推奨事項を提供するサービス。
* コスト最適化
* パフォーマンス
* セキュリティー
* フォールトトレランス（耐障害性）
* サービス制限

ビジネスサポートプラン以降で全部利用できる。

## 移行、転送

### AWS Database Migration Service (AWS DMS)

### AWS DataSync

オンプレミスとEFS間のデータを迅速に転送できるマネージドサービス。  
オープンソースのツールと比べ約10倍の速度でインターネットもしくはDirectConnect経由で転送できる。

### AWS Migration Hub

### AWS Server Migration Service (SMS)

### AWS Snowball

### AWS Transfer Family


## ネットワーク、コンテンツ配信

### Amazon API Gateway

* APIを生成・管理することが可能。
* Web Socketを利用して双方向通信が可能。
* EC2 / Lambda / その他Webアプリケーションのワークロード処理を実行できる約10万個のAPI同時呼び出し・受付が可能。

### CloudFront

https://d1.awsstatic.com/webinars/jp/pdf/services/20190730_AWS-BlackBelt_Amazon_CloudFront.pdf  
https://www.youtube.com/watch?v=mmRKzzOvJJY

課金対象  
* AWSからのデータ転送アウト
* ユーザからのリクエストの数と種類、リクエストが行われた地域
* トラフィック分散

独自ドメインを設定可能。

### AWS Direct Connect

  AWSとデータセンターと専用線で接続する。

* Direct Connect Gateway
  Direct Connect経由で別のAWSアカウントのVPC

### Global Accelerator

地理的に近いエンドポイントにTCP/UDPトラフィックを最適にルーティングする。

### Route53

名前解決を行うネームサーバをマネージドで提供するサービス。  

* Public Hosted Zone  
インターネット上に公開されたDNSドメインのレコードを管理するコンテナ。

* Private Hosted Zone  
VPCに閉じたプライベートネットワーク内のDNSドメインのレコードを管理するコンテナ。

複数のルーティングポリシーがある。

* シンプルルーティング  
通常のDNSレコードによるルーティング。  
同じ名前の複数のレコードは設定できないが、一つの名前に複数の値を設定でき、リゾルバはランダムな値を返す。
* 位置情報ルーティング  
ユーザの位置情報に基づいてルーティングする。  
日本からのアクセスは日本語コンテンツが配置されたWebサーバーに接続するという制御が可能。
* フェイルオーバー
* 地理的接近性
* レイテンシー
* 複数回答値
* 加重


#### Resolver

VPCに標準で備わるDNSサーバー。

#### Resolver for Hybrid Clouds

オンプレとVPC間の名前解決を行う。

* オンプレ → VPC
* オンプレ → インターネット
* VPC ｈ→ オンプレ

#### トラフィックフロー

複雑で大規模なレコードの作成・ルーティングを順序を用いて簡略化できる。

### AWS Transit Gateway
  複数のVPCとオンプレを中央ハブを介して接続するサービス。

### VPC (Amazon Virtual Private Cloud）

#### インターネットゲートウェイ(IGW)
#### 仮想プライベートゲートウェイ(PGW)
#### マルチAZ  
同一の役割を持ったサブネットを複数のAZにそれぞれ作成する。

#### パブリックサブネット  
ルーティングで直接接続しているサブネット。  
グローバルIPを設定したEC2等やNATゲートウェイを配置する。

#### プライベートサブネット  
ルーティングが直接インターネットに接続していないサブネット。

#### NATゲートウェイ  
グローバルIPを持つ。プライベートIPをNATゲートウェイが持つグローバルIPに変換して外部と通信する。  
パブリックサブネットに配置する。

#### セキュリティグループ(SG)  
ファイアウォール相当。  
ステートフルなので、レスポンスを考慮しなくてもよい。  
ネットワークACLの次に評価される。
ACLとは違い、全てのルールが適用される。
許可ルールのみ設定する。

#### ネットワークACL(Access Control List)  
タイプ・プロトコル・ポート・IP・送受信でアクセスを制御（許可/拒否）を設定する。
ステートレスなので、レスポンスも明示的に指定する必要あり。  
サブネット単位に有効。

#### VPCエンドポイント
  * ゲートウェイポイント  
    S3やDynamoDBなどのAWSサービスと接続するゲートウェイエンドポイント。
  * AWS PrivateLink
    トラフィックをパブリックインターネットをに公開せずVPC・AWSサービス・オンプレと接続するサービス。

#### VPC Peering
  2つのVPCをプライベートに接続する機能。  
  別のリージョン、別のAWSアカウントのVPCとも接続可能。  
  中国リージョンとは接続できない。

#### VPCフローログ  
  ENI(AWSの仮想NIC。Elastic Network Interface,ENI)単位に記録されるネットワークログ。

#### NLB

* L4ロードバランサ
* 毎秒数百万のリクエストに対応。

#### Site-to-Site VPN(サイト間VPN)

https://docs.aws.amazon.com/ja_jp/vpn/latest/s2svpn/VPC_VPN.html

VPCとオンプレミスネットワーク間の接続。  
IPSecがサポートされている。

VPCはデフォルトではインターネットと通信できないが、サイト間VPNを利用すると通信できる。



## セキュリティ、アイデンティティ、コンプライアンス

### AWS Certificate Manager

### AWS Directory Service

* Simple ADにより新規ディレクトリを作成する。
* MS Active DirectoryをAWS上に構築できる。

#### AD Connector

既存のエンタープライズディレクトリに接続できる。


### Amazon GuardDuty

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

### Amazon Inspector

自動的にアプリケーションに対し、露出・脆弱性・ベストプラクティスからの逸脱がないかどうか確認できる。

### AWS Key Management Service(KMS)

新しいマスターキーを作成し、誰がアクセスできるか、どのサービスで利用できるか、管理するサービス。

CloudHSM

#### カスタマーキー（CMK）

データ暗号化キーのアクセスを制御するために使用する。

### Amazon Macie

### AWS Secrets Manager

### AWS Shield

### AWS Single Sign-On

### AWS WAF

ウェブアプリケーションのファイアウォール。

* Referer制限

  外部からURLを直接参照することを制限することができる。

## ストレージ

### EBS

* インスタンスストア  
スループットが早い。揮発性でEC2を終了するとデータが消える。

* スナップショット
  * S3にバックアップを保存する。
  * 増分バックアップ。  
    * 前回から変更されたブロックのみ保存されるので、スナップショットに必要な時間が最小限となる。
    * 世代管理が可能。
  * 圧縮されるので課金は最低限で済む。
  * 別のAZに復元可能。

### EFS

NFSv4(Network File System)プロトコルによるデータ転送をサポートしている。


### FSx


### S3

可用性と耐久性が高いストレージサービス。

#### ストレージクラス

* Standart(標準)

* Intelligent-Tiering  

  アクセスパターンに応じて自動的にコストを削減する。  
頻繁・低頻度・アーカイブ・ディープアーカイブの4層をもち、アクセスパターンによって、自動的にデータを移動する。

* 低頻度アクセス（標準 - AI)  

  格納コストが安価で、頻繁にアクセスしないが高速なアクセスが必要な場合に使う。

* 1ゾーン・低頻度アクセス（1ゾーン - AI）

  1AZにデータを保存。  
  可用性が低くなるが低コスト。

* Glacier

  低コストで長期保存。  
  データ取り出しには事前にリクエストが必要で、取り出し可能になるまで数分〜数時間かかる。

  |データ取得タイプ|特徴|
  |---|---|
  |迅速取り出し|1〜5分以内ß
  |標準取り出し|3〜5時間以内で全てのアーカイブにアクセス可能
  |大量取り出し|大量データを1日以内で取得可能。5〜12時間必要。

* Glacier Deep　Archive

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


## ソリューションアーキテクト範囲外？

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


### SWF / Step Function

### SES

### CodeCommit

### CodeBuild

### CodeDeploy

### CodePipeline

### コンシェルジュ

エンタープライズサポートプラン。

### プロフェッショナルサービス

### サポート

#### ベーシックサポート
無料。  
ホワイトメーパー、ドキュメント、サポートコミュニティを利用できる。

#### デベロッパーサポート
* ベストプラクティスのガイダンス
* クライアント側の診断ツール
* 基盤となるアーキテクチャのサポート。製品、機能サービスの使用方法をガイダンス。  
サービスや機能の組み合わせを特定するのに役立つ。

#### ビジネスサポート
* 特定のニーズを適切にサポートできるAWS製品・機能・サービスを特定するためのユースケースガイダンス。
* Trusted Advisorの全てのチェック。
* 一般的なOS、アプリケーションなど、サードパーティソフトウェアの限定的サポート。

#### エンタープライズサポートプラン

* 特定のユースケースとアプリケーションを支援するコンサルティング。
* Infractructure Event Management  
AWSエキスパートがイベント計画に関わり、アーキテクチャやスケーリング、運用に関するガイダンスやアプローチを提供する。
* テクニカルアカウントマネージャー（TAM）  
アプリケーションの計画、デプロイ、最適化に関するガイダンスやレビューを提供する。  
ユーザと継続的に連絡をとる。
