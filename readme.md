# AWS認定ソリューションアーキテクトアソシエイト対策

AWS ドキュメント  
https://docs.aws.amazon.com/ja_jp/

## 目次

<!-- TOC -->

- [AWS認定ソリューションアーキテクトアソシエイト対策](#aws認定ソリューションアーキテクトアソシエイト対策)
    - [目次](#目次)
    - [AWS Well-Architected](#aws-well-architected)
        - [運用上の優秀性（Operational Exellence）](#運用上の優秀性operational-exellence)
        - [セキュリティ（Security）](#セキュリティsecurity)
            - [責任共有モデル](#責任共有モデル)
        - [信頼性（Reliability）](#信頼性reliability)
            - [用語](#用語)
            - [DR戦略](#dr戦略)
        - [パフォーマンス効率（Performance Efficiency）](#パフォーマンス効率performance-efficiency)
        - [コスト最適化（Cost Optimization）](#コスト最適化cost-optimization)
    - [グローバルインフラストラクチャ](#グローバルインフラストラクチャ)
        - [リージョン](#リージョン)
        - [アベイラビリティーゾーン（AZ）](#アベイラビリティーゾーンaz)
    - [分析・アナリティクス](#分析・アナリティクス)
        - [Athena](#athena)
        - [Elasticsearch Service(AWS ES)](#elasticsearch-serviceaws-es)
        - [EMR](#emr)
        - [Glue](#glue)
        - [Kinesis](#kinesis)
            - [Data Stream](#data-stream)
            - [Data Firehose](#data-firehose)
            - [Data Analytics](#data-analytics)
            - [Agent](#agent)
        - [Quick Sight](#quick-sight)
        - [Data PipeLine](#data-pipeline)
    - [AWS の請求情報とコスト管理](#aws-の請求情報とコスト管理)
        - [AWS料金計算ツール（AWS Pricing Calculator）](#aws料金計算ツールaws-pricing-calculator)
        - [請求ダッシュボード](#請求ダッシュボード)
            - [Budgets](#budgets)
            - [Cost Exproler](#cost-exproler)
    - [アプリケーション統合](#アプリケーション統合)
        - [SNS(Simple Notification Service)](#snssimple-notification-service)
        - [SQS](#sqs)
            - [可視性タイムアウト](#可視性タイムアウト)
    - [コンピューティング](#コンピューティング)
        - [EC2](#ec2)
            - [インスタンス購入オプション](#インスタンス購入オプション)
            - [スポットインスタンス](#スポットインスタンス)
            - [ストレージ](#ストレージ)
            - [AMI](#ami)
            - [ブートストラップ](#ブートストラップ)
            - [ゴールデンイメージ](#ゴールデンイメージ)
            - [Auto Scaling](#auto-scaling)
        - [Elastic Beanstalk](#elastic-beanstalk)
        - [Lambda](#lambda)
    - [コンテナ](#コンテナ)
        - [AWS Fargate](#aws-fargate)
        - [ECS](#ecs)
        - [EKS](#eks)
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
            - [SCP サービスコントロールポリシー](#scp-サービスコントロールポリシー)
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
            - [キャッシュする期間](#キャッシュする期間)
            - [コンテンツへのアクセス制限](#コンテンツへのアクセス制限)
        - [AWS Direct Connect](#aws-direct-connect)
        - [Global Accelerator](#global-accelerator)
        - [Route53](#route53)
            - [レコード](#レコード)
            - [Resolver](#resolver)
            - [Resolver for Hybrid Clouds](#resolver-for-hybrid-clouds)
            - [トラフィックフロー](#トラフィックフロー)
        - [AWS Transit Gateway](#aws-transit-gateway)
        - [VPC (Amazon Virtual Private Cloud）](#vpc-amazon-virtual-private-cloud)
            - [インターネットゲートウェイ(IGW)](#インターネットゲートウェイigw)
            - [仮想プライベートゲートウェイ(PGW)](#仮想プライベートゲートウェイpgw)
            - [マルチAZ](#マルチaz)
            - [Elastic IPアドレス](#elastic-ipアドレス)
            - [CIDR（サイダー）](#cidrサイダー)
            - [パブリックサブネット](#パブリックサブネット)
            - [プライベートサブネット](#プライベートサブネット)
            - [NATインスタンス](#natインスタンス)
            - [NATゲートウェイ](#natゲートウェイ)
            - [DNS属性](#dns属性)
            - [セキュリティグループ(SG)](#セキュリティグループsg)
            - [ネットワークACL(Access Control List)](#ネットワークaclaccess-control-list)
            - [VPCエンドポイント](#vpcエンドポイント)
            - [VPC Peering](#vpc-peering)
            - [VPCフローログ](#vpcフローログ)
            - [NLB](#nlb)
            - [Site-to-Site VPN(サイト間VPN)](#site-to-site-vpnサイト間vpn)
        - [ELB](#elb)
            - [Clasic Load Balancer](#clasic-load-balancer)
            - [Application Load Balancer](#application-load-balancer)
            - [Network Load Balancer](#network-load-balancer)
            - [Gateway Load Balancer](#gateway-load-balancer)
            - [ELBの機能](#elbの機能)
    - [セキュリティ、アイデンティティ、コンプライアンス](#セキュリティアイデンティティコンプライアンス)
        - [AWS Certificate Manager](#aws-certificate-manager)
        - [AWS Directory Service](#aws-directory-service)
            - [AD Connector](#ad-connector)
        - [Amazon GuardDuty](#amazon-guardduty)
        - [IAM](#iam)
        - [Cognito](#cognito)
        - [Amazon Inspector](#amazon-inspector)
        - [AWS Key Management Service(KMS)](#aws-key-management-servicekms)
            - [カスタマーキー（CMK）](#カスタマーキーcmk)
        - [CloudHSM](#cloudhsm)
        - [Amazon Macie](#amazon-macie)
        - [AWS Secrets Manager](#aws-secrets-manager)
        - [AWS Shield](#aws-shield)
        - [AWS Single Sign-On](#aws-single-sign-on)
        - [AWS WAF](#aws-waf)
    - [ストレージ](#ストレージ)
        - [EBS](#ebs)
            - [種類](#種類)
            - [インスタンスストア](#インスタンスストア)
            - [スナップショット](#スナップショット)
        - [EFS](#efs)
        - [FSx](#fsx)
        - [S3](#s3)
            - [ストレージクラス](#ストレージクラス)
            - [暗号化](#暗号化)
            - [S3 Select](#s3-select)
            - [オブジェクトロック](#オブジェクトロック)
            - [レプリケーション](#レプリケーション)
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

#### 用語

* DR - Disaster RecoveryDisaster

  災害対策。
  
* 目標復旧時間(RTO - Recovery Time Objective)
* 目標復旧地点(RPO - Recovery Point Objective)

#### DR戦略

* バックアップと復元

  データをアプリケーションをDRリージョンにバックアップし、復元する。

  RPOは時間単位。RTOは24時間以内。

* パイロットライト

  DRリージョンに停止した状態のサーバを用意しておき、災害発生時に切り替える。

  RPOは分、RTOは時間。

* ウォームスタンバイ

  DRリージョンでスケールダウンされた完全に機能するワークロードを常にONの状態で維持する。
  
  RPOは秒、RTOは分。

* マルチリージョン アクティブ-アクティブ

  ワークロードが複数のリージョンにデプロイされ、動作させる。  
  データを同期させる必要がある。  
  データの破壊や破損からユーザを守ることはできない。

  RPOは0に近く、RTOも0になる可能性がある。

### パフォーマンス効率（Performance Efficiency）

### コスト最適化（Cost Optimization）


## グローバルインフラストラクチャ

### リージョン

### アベイラビリティーゾーン（AZ）

リージョン内のアベイラビリティーゾーンは低遅延リンクで接続されており、AZ間のデータ同期を低遅延で実現している。




## 分析・アナリティクス

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

#### Data Stream

あらゆる規模のデータストリームをキャプチャ・処理・保存することを可能とする。

IoTなど、次々に送られてくるデータを別のサービスに届けるサービス。

* プロデューサー  
  Data Streamへの入力元。

* コンシューマー  
  Data Streamからの出力先。  
  S3、DynamoDB、Redshift、EMR、Kinesis FirehoseFirehose。

* データストリーム  
  シャードのかたまり。各シャードには一連のデータレコードがある。
  
* データレコード  
  保存されるデータの単位。シーケンス番号、パーティションキー、blobデータで構成される。blobデータは1MB。

* キャパシティモード  
  容量の管理方法と課金方法。  
  オンデマンドモードとプロビジョニングモードがある。

  * オンデマンドモード  
    必要なスループットを提供するためにシャードを自動的に管理する。使用する実際のスループットに対して課金される。

  * プロビジョニングモード  
    シャード数を指定する。
    シャード合計容量のスループットに対し1時間ごとに課金される。

* シャード  
  ストリーム内の一意に識別されたデータレコードのシーケンス。

* パーティションキー  
  シャードごとにデータをグループ化するために使用される。データレコードのパーティションキーからそのデータレコードが属するシャードを特定する。

* シーケンス番号  
  シャード内のパーティションキーごとの一意の番号。

* サーバ側暗号化  
  プロデューサーから入力したデータを自動的に暗号化できる。  
  暗号化はAWS KMSのマスターキーを使用する。
  
#### Data Firehose

ストリーミングを確実にキャプチャ、変換し、データレイク・データストア・分析サービスに配信するELTサービス。  
配信されたストリーミングは、Athena・Redshift・その他分析ツールで解析する。

概念図：  
https://aws.amazon.com/jp/kinesis/data-firehose/


* データ採取  
  AWS SDK、Amazon Kinesis Data Stream、Amazon Kinesis AgentなどのAWSサービス。または、オープンソースエージェント。

* 変換  
  AWS Lambdaで変換できる。

* 配信  
  S3、Redshift、OpenSerch、Splunk（データ分析サービス）、HTTPエンドポイント。

#### Data Analytics

ストリームデータのリアルタイム解析を行う。

#### Agent

ストリーミングデータを収集して取り込む仕組みをアプリケーションに実装できる。

### Quick Sight

### Data PipeLine

AWSデータベースやストレージ間のデータ移動や変換を自動化するサービス。  
定期的な動作が可能。

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

処理を分散できるので、負荷分散を可能にする。  
また、AWSリソースの水平スケーリングが可能となる。

* 遅延キュー

* 優先度付きキュー

* デットレターキュー  
正常処理できないキューを別のキューへ移動させる。  

#### 可視性タイムアウト

特定のキューが複数のコンシューマーに処理されないようにする。  
キューがコンシューマーに処理されると、そのキューが他のコンシューマーから見えなくなる。


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

* Dedicated Host  
専用の物理サーバにEC2インスタンスを起動する。  
最も高価なオプション。  
ホストへのインスタンス配置を制御できる。

* ハードウェア占有インスタンス（Didicated Instance）  
専用の物理サーバにEC2インスタンスを起動する。
ホストへのインスタンス配置を制御できない。

* キャパシティ予約

  特定のアベイラビリティゾーンで任意の時間だけコンピューティング能力を予約できる。

#### スポットインスタンス

キャパシティの空き具合によって最大90％の割引。  
空きがなくなると中断される可能性がある。

#### ストレージ

EBS と インスタンスストアが利用できる。

DeleteOnTermination属性で、EC2インスタンス終了時にEBSも削除するかどうか設定する。 
ルートボリュームではデフォルトで有効化されているので、EC2終了時に削除される。

#### AMI

Amazon Machine Image。

* EBS-backed AMI  
  ルートデバイスがEBSスナップショットから作成されるEBSボリューム。

* Instance Store-backed AMI
  ルートデバイスが、S3に保存されたテンプレートから作成されたインスタンスストアボリューム。
  起動に時間がかかる。

#### ブートストラップ

EC2起動時に自動ブートストラップスクリプトを実行し、ソフトウェアをインストールしたり、データコピーである特定の状態にしたりできる。

#### ゴールデンイメージ

そのリソースの最適な状態を保存したAMIやスナップショット。

#### Auto Scaling

* クールダウン

  デフォルト期間は300秒。
  
  スケールアウトのインスタンス起動時に、新しいインスタンスの起動が完了するまでの間、再度スケールアウトしてしまうことをことを防ぐ。  
  起動開始（スケーリングタスク）後、300秒の間はスケールアウト閾値を超えていてもスケールアウトしない。

  逆も然り、スケールイン開始後、300秒の間はスケールイン閾値を下回ってもスケールアウトしない。

### Elastic Beanstalk

アプリケーションを素早くデプロイし管理を自動化できる。  
Git・IDEからアプリケーションをアップロードするだけで、デプロイの詳細（容量プロビジョニング、負荷分散、AutoScaling、アプリケーションのヘルスモニタリングなど）を処理する。

ECSなどDockerにホストされたアプリケーションの展開もサポートしている。 
ECSやEKSと連携してDocker経由でアプリケーションの展開を設定しつつ、バージョン管理や状態監視を自動化できる。

### Lambda

* 課金要素は利用時間とリクエスト数。

## コンテナ

### AWS Fargate

ESC,EKS(Elastic Kubernetes Service)で動作するコンテナ向けサーバレスコンピューティングエンジン。

### ECS

### EKS

Elastic Kubernetes Service

コンテナ化されたアプリケーションのデプロイ、スケーリング、管理を自動化するためのオープンソースシステム。

EC2起動モードとFargate起動モードがある。


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

* IAMデータベース認証

  対象RDS

  * MariaDB
  * MySQL
  * PostgreSQL

  利用

    AWS CLI、AWS SDKから利用可能。

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

* 拡張VPCルーティング

  クラスターとデータリポジトリ間の全てのCOPY・UNLOADトラフィックをVPC経由に強制できる。 
  これと、VPCフローログを利用することで、Redshiftのトラフィックを監視できる。
  

### dynamoDB

* グローバルテーブル  
グローバルに展開されたアプリケーションに対して高速読み取りを提供するレプリケーションの仕組み。  
マルチリージョンにマルチマスターデータベースをデプロイする。  
グローバルなユーザに低レイテンシーアクセスを提供する。

* dynamoDB Accelerator(DAX)  
インメモリキャッシュ。  
ミリセコンドからマイクロセコンドへの最大10倍のパフォーマンスを向上できる。  
常時パフォーマンスが向上するが、コストは高め。

* dynamoDB ストリーム

テーブル変更などをトリガーにLambdaなどを起動する。

* dynamoDb Auto Scaling

テーブルとインデックスを監視して、アプリケーションのトラフィックにあわせてスロットリングなしで自動的にスループットを調整する。  
これにより一時的な負荷に対してパフォーマンス管理が容易となり、アプリケーション可用性を維持しつつコストを抑えることができる。

#### 読み込み整合性

* 結果生合成のある読み込み  
最新の書き込み結果が反映されない場合がある。

* 強い生合成のある読み込み  
全ての書き込みが完了したデータを読み取る。  
GSIでは利用不可。

#### 料金

* 同じリージョンのAZ間のデータ転送は無料。
* リージョン間のデータ転送は、送受信リージョン双方に課金される。

### Aurora

マルチAZにまたがって仮想ボリュームが構成されている。


### ElastiCahce

完全マネージド型インメモリデータベース。  
高速リアルタイム処理、トランザクションが可能。  
KVS(Key-Valueストア)

* ユースケース
  * インメモリデータストア  
    データのコピーに超高速で低コストなアクセス。
  * ゲームのリーダーボード
  * レコメンテーション

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

#### SCP サービスコントロールポリシー

AWSアカウントまたはOU（組織単位）に対してAWSサービスへの権限境界を設定できる。  

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

#### キャッシュする期間

* TTL

  CloudFront配信時に設定されるキャッシュ保持時間。
  
* オリジンが Cache-control: max-age ディレクティブをオブジェクトに設定する。

  オリジンから取得したオブジェクトに、そのオブジェクトのキャッシュ期間を指定する。


#### コンテンツへのアクセス制限

特定のユーザに対してのみコンテンツへのアクセスを許可する機能。

* 署名付きURL

  ユーザがアクセス許可を要求した際、アプリケーションがユーザのアクセス権を確認して、署名付きURLを返却する。  
  コンテンツのURLは署名付きURLに変更される。

* 署名付きCookie

  ユーザがアプリケーションにアクセスした際、署名付きCoockieを発行する。 
  制限コンテンツアクセスの際、リクエストヘッダの署名付きCoockiesによってアクセスを制限する。  
  コンテンツのURLは変わらない。



### AWS Direct Connect

  AWSとデータセンターと専用線で接続する。

* Direct Connect Gateway
  Direct Connect経由で別のAWSアカウントのVPC

### Global Accelerator

地理的に近いエンドポイントにTCP/UDPトラフィックを最適にルーティングする。

* BYOIP(Bring Your Own IP)

  自身が保有するIPアドレスをAWSのサービスに割り当てることができる。

  RIR(Region Internet Registry。地域のIPアドレスの割り当てを行うレジストリ(登記所))から、ROA(Remote Origin Authorization)オブジェクトを作成する。
  ROAを使って、IPアドレスをAWSサービスに紐づける。

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

  * アクティブ／パッシブ  
    通常はプライマリリソースにルーティングする。  
    プライマリリソースに障害が発生した場合に、セカンダリリソースにルーティングする。  
    フェールオーバーポリシーを利用する。

  * アクティブ／アクティブ
    通常は複数のリソースをアクティブにし、フェールオーバー以外のルーティングポリシーを使う。  
    障害が発生した場合、正常なリソースにフェイルバックする。
  
* 地理的接近性
* レイテンシー
* 複数回答値
* 加重

####　レコード

* ALIASレコード

  DNSクエリにAWSサービスのエンドポイントのIPアドレスを返答することで、AWSリソースにドメイン名を設定できる。

#### Resolver

VPCに標準で備わるDNSサーバー。

#### Resolver for Hybrid Clouds

オンプレとVPC間の名前解決を行う。

* オンプレ → VPC
* オンプレ → インターネット
* VPC → オンプレ

#### トラフィックフロー

複雑で大規模なレコードの作成・ルーティングを順序を用いて簡略化できる。

### AWS Transit Gateway
  複数のVPCとオンプレを中央ハブを介して接続するサービス。

### VPC (Amazon Virtual Private Cloud）

#### インターネットゲートウェイ(IGW)
#### 仮想プライベートゲートウェイ(PGW)
#### マルチAZ  
同一の役割を持ったサブネットを複数のAZにそれぞれ作成する。

#### Elastic IPアドレス

* 固定のIPアドレスを利用できる。

* EC2とNAT Gatewayに設定可能。  

  連携先がIPアドレス制限を行なっている場合、NAT GatewayにEIPで固定IPにすることでAWSリソースから連携先にアクセスできる。

* インスタンスに割り当てられていない場合に料金が発生する。

* EC2のパブリックIPアドレスは無料で利用できるが、インスタンスを開始するたびにIPアドレスが変わってしまう。これを固定にするには Elastic IPアドレスを利用する。

#### CIDR（サイダー）

クラスレスなネットワーク/IPアドレス割り当て方法で、任意のブロックで割り当てられる。
逆に、決められたブロックで割り当てられるのがクラスフル（クラスA、クラスB、クラスC）。

例：

|サブネットマスク|IPアドレス数|
|---|---|
|/26|1024|
|/24|256|
|/26|64|
|/28|16|

よく割り当てるのが/24で256。サブネットが2単位にIPアドレス数が4倍変化すると覚える。

#### パブリックサブネット  
ルーティングで直接接続しているサブネット。  
グローバルIPを設定したEC2等やNATゲートウェイを配置する。

#### プライベートサブネット  
ルーティングが直接インターネットに接続していないサブネット。

#### NATインスタンス

ネットワークアドレス変換を提供する独自のAMI。

現在はNATゲートウェイの利用が推奨されている。

#### NATゲートウェイ  
グローバルIPを持つ。プライベートIPをNATゲートウェイが持つグローバルIPに変換して外部と通信する。  
パブリックサブネットに配置する。

#### DNS属性

パブリックIPアドレスを持つインスタンスへのパブリックDNSホスト名の割り当てを行うかどうか設定する。

#### セキュリティグループ(SG)  
ファイアウォール相当。  
ステートフルなので、レスポンスを考慮しなくてもよい。  
ネットワークACLの次に評価される。
ACLとは違い、全てのルールが適用される。
許可ルールのみ設定する。

設定反映は即時。


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

### ELB

受信したトラフィックを複数のAZの複数ターゲット（EC2、コンテナ、IPアドレスなど）に振り分ける。

#### Clasic Load Balancer

L4/L7対応ロードバランサー。
古いタイプのロードバランサーでALB、NLBが優先。

#### Application Load Balancer

L7対応ロードバランサー。

#### Network Load Balancer

L4 NAT　ロードバランサー。  
毎秒数百万回のリクエストを処理できる高性能ロードバランサー。大規模システム向け。

#### Gateway Load Balancer

#### ELBの機能

* Connection Draining

  インスタンスが異常検知か登録解除されたときに、そのインスタンスに新しいリクエストを送信しないようにする。

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

### Cognito

アプリケーションにユーザ認証機能を提供する。

Googleアカウントなどからのソーシャルサインインや、Active DirectoryなどのSAML IDプロバイダーでのサインインが可能。

### Amazon Inspector

自動的にアプリケーションに対し、露出・脆弱性・ベストプラクティスからの逸脱がないかどうか確認できる。

### AWS Key Management Service(KMS)

新しいマスターキーを作成し、誰がアクセスできるか、どのサービスで利用できるか、管理するサービス。


#### カスタマーキー（CMK）

データ暗号化キーのアクセスを制御するために使用する。

### CloudHSM

クラウドベースのハードウェアセキュリティモジュール（HSM）

米国のセキュリティ基準 FIPS-140-2 レベル3標準に準拠している。


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

#### 種類

|項目|コールドHDD|スループット最適化HDD|汎用SSD|プロビジョンドIOPS|プロビジョンドIOPS io2 Block Express|
|---|---|---|---|---|---|
|サイズ|125GiB-16TiB|125GiB-16TiB|1GiB-16TiB|4GiB-16TiB|4GiB-16TiB|
|最大IOPS|250|500|16,000|64,000|256,000|
|スループット(MiB/s)|250|500|250-1,000|1,000|4,000

上記の他に、「マグネティック（旧世代）」がある。

#### インスタンスストア  
スループットが早い。揮発性でEC2を終了するとデータが消える。  
無料。

#### スナップショット
  * S3にバックアップを保存する。
  * 自動的に暗号化される。
  * 増分バックアップ。  
    * 前回から変更されたブロックのみ保存されるので、スナップショットに必要な時間が最小限となる。
    * 世代管理が可能。
  * スナップショットの作成はConsoleかAWS CLIから手動で行う。  
    自動化する場合はData Lifecycle Managerを利用する。
  * 圧縮されるので課金は最低限で済む。
  * 別のAZに復元可能。

* Data Lifecycle Manager（DLM）

  スナップショットとAMIの作成・保持・削除を自動化できる。


### EFS

NFSv4(Network File System)プロトコルによるデータ転送をサポートしている。


### FSx


### S3

可用性と耐久性が高いストレージサービス。

#### ストレージクラス

* Standard(標準)

* Standard IA（標準 - 低頻度アクセス)  

  格納コストが安価で、頻繁にアクセスしないが高速なアクセスが必要な場合に使う。

* One Zone IA（1ゾーン・低頻度アクセス）

  1AZにデータを保存。  
  可用性が低くなるが低コスト。

* Glacier

  低コストで長期保存。  
  データ取り出しには事前にリクエストが必要で、取り出し可能になるまで数分〜数時間かかる。

  * Instant Retrieval

    4半期に一度のアクセス頻度。  
    ms単位の取り出しが必要。  
    用途は医療画像、健康記録、ニュースメディア、衛星画像、航空家蔵など。  
    Standard IAよりも保存料金が安いが、取り出し料金は少し高い。

  * Flexible Retrieval

    年に1・2回のアクセス頻度。
    取り出しには、数分または、5〜12時間。5〜12時間の取り出しは無料。  
    DRやバックアップ。
    Instant Retrievalよりも安い。

    |データ取得タイプ|特徴|
    |---|---|
    |迅速取り出し|1〜5分以内
    |標準取り出し|3〜5時間以内で全てのアーカイブにアクセス可能
    |大量取り出し|大量データを1日以内で取得可能。5〜12時間必要。


  * Glacier Deep Archive

    年に1・2回のアクセス頻度。7〜10年の保存期間が求められるもの向け。  
    取り出し可能になるまで、最大12h。  
    最も低コスト。

* Intelligent-Tiering  

  アクセスパターンに応じて自動的にコストを削減する。  
  頻繁・低頻度・アーカイブ・ディープアーカイブの4層をもち、アクセスパターンによって、自動的にデータを移動する。


#### 暗号化

* サーバ側暗号化

  S3に保管するときに暗号化し、取得時に自動的に復号化する。  

  * SSE-S3  
    S3で管理されたキー（SSE-S3）を使用する。  
    暗号化はAES-256を利用。

  * SSE-KMS  
    KWS-KMSで管理されたキーを使用する。

  * SSE-C  
    ユーザが指定したキーで暗号化する。

* クライアント側暗号化

  クライアント側で暗号化しS3に格納する。  
  S3側に設定があるわけではない。  
  暗号化キー・暗号プロセスはクライアント側が管理する。  

#### S3 Select

SQLでS3コンテンツをフィルタリングし、必要なサブセットを取得できる。これにより、転送データ量を減らし、コストとレイテンシーを削減できる。

#### オブジェクトロック

オブジェクトを一定期間、削除・上書きを防止する。

#### レプリケーション

* 同一リージョン、異なるリージョンにレプリケーション可能。
* 異なるストレージクラスへのレプリケーションが可能。
* レプリケーションを設定してしまえば、オブジェクトの作成・更新・削除の際に自動的に行われる。
* レプリケーション時のデータ転送には費用が発生する。

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
