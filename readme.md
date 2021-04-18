# AWS認定ソリューションアーキテクトアソシエイト対策

* 試験ガイド  
https://d1.awsstatic.com/ja_JP/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf

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
* ネットワークACL(Access Control List)

* VPCエンドポイント

## 共通用語

* 単一障害点  
Single Point Of Failure(SPOF)