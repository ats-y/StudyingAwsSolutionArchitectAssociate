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
    - [コンピューティングサービス](#コンピューティングサービス)
        - [EC2](#ec2)
        - [ELB](#elb)
        - [ECS](#ecs)
        - [Lambda](#lambda)
    - [運用支援サービス](#運用支援サービス)
        - [CloudWatch](#cloudwatch)
        - [CloudTail](#cloudtail)
    - [ストレージサービス](#ストレージサービス)
        - [EBS](#ebs)
        - [EFS](#efs)
        - [S3](#s3)
        - [S3 Glacier](#s3-glacier)
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
        - [KMS / CloudHSM](#kms--cloudhsm)
        - [AWS Certificate Manager](#aws-certificate-manager)
    - [アプリケーションサービス](#アプリケーションサービス)
        - [SQS](#sqs)
        - [SWF / Step Function](#swf--step-function)
        - [SNS / SES](#sns--ses)
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
        - [EMR](#emr)
        - [ELT](#elt)
        - [その他](#その他)
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

### Route53

* 位置情報ルーティングポリシー  
ユーザの位置情報に基づいてルーティングする。  
日本からのアクセスは日本語コンテンツが配置されたWebサーバーに接続するという制御が可能。

## コンピューティングサービス

### EC2

### ELB

### ECS

### Lambda

## 運用支援サービス

### CloudWatch

### CloudTail

## ストレージサービス

### EBS

### EFS

NFSv4(Network File System)プロトコルによるデータ転送をサポートしている。

### S3


### S3 Glacier

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

### KMS / CloudHSM

### AWS Certificate Manager

## アプリケーションサービス

### SQS

### SWF / Step Function

### SNS / SES

## 開発者ツール

### CodeCommit

### CodeBuild

### CodeDeploy

### CodePipeline

## プロビジョニングサービス

### Elastic Beanstalk

### OpsWorks

### CloudFormation

## 分析サービス

### EMR

### ELT

### その他

## アーキテクチャ設計


## 共通用語

* 単一障害点  
Single Point Of Failure(SPOF)