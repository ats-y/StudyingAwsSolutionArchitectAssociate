# AWS認定ソリューションアーキテクトアソシエイト対策

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



## 共通用語

* 単一障害点  
Single Point Of Failure(SPOF)