---
casestudy:
  title: 'ケーススタディ: 規制コンプライアンスを評価する'
  module: 'Module 4: Evaluate a regulatory compliance strategy'
---

このケース スタディ演習は、このモジュールで学習した内容に関連するいくつかの概念設計タスクの実行を経験できるように設計されています。

## <a name="case-study-evaluate-regulatory-compliance"></a>ケース スタディ: 規制コンプライアンスを評価する

Contoso Pharma is an international pharmaceutical industry with a presence in North America and Europe. Contoso Pharma has workloads on-premises and in Azure. The goal is that in the next two years, all workloads will be fully in Azure and there will be minimum workloads on-premises. Below is a list of their major workloads:

- VM (Windows と Linux)
- ストレージ アカウント
- Key Vault
- VM 上の SQL PaaS と SQL

Contoso Pharma also has a Site-to-Site VPN between the headquarters in Redmond and the main office in London. This VPN is used to allow resources on-premises to communicate.

Contoso Pharma has a legacy environment in Redmond composed by a couple of Windows Server 2012 running a Web Server that is used by the application that queries the database to check for customer's information. Upon investigation it was noted that the communication of the legacy web server with the database is done via HTTP.

### <a name="design-requirements"></a>設計の要件

Contoso Pharma には、次の表に示すように、ワークロードに応じて異なるコンプライアンス ニーズがあります。

| **[ワークロード]** | **データの種類** | **コンプライアンス標準** |
|:---:|:---:|:---:|
| Windows VM | クレジット カード名義人情報 | PCI DSS |
| SQL PaaS | 患者の健康情報 | HIPAA |
| ストレージ アカウント | クレジット カード名義人情報 | PCI DSS アカウント |

これらの標準に準拠するために、Contoso Pharma は次のことができる必要があります。

- コンプライアンスの進行状況を経時的に監視する
- ワークロード所有者がそれらの標準に準拠していないリソースをプロビジョニングすることを禁止する
- 環境にデプロイされる新しいサブスクリプションが、必要な標準を既定で使用していることを確認する
- 各地理的な場所にプロビジョニングされるリソースが、データ主権のためにソース リージョンにデータを保持していることを確認する

### <a name="design-tasks"></a>設計タスク

* To ensure that Contoso Pharma can analyze their compliance status over time, which tool should be utilized? Select the most appropriate option.
* ワークロードの所有者が必要な標準に従っているリソースのみを作成するように強制するには、Azure のどのサービスを使用する必要がありますか?
* ワークロードの所有者がリソースを作成するときに、データが正しい地理的な場所に保持されるようにするには、どのオプションを使用する必要がありますか?
* Contoso Pharma は、プロビジョニングされた VM が PCI DSS に準拠しているかどうかをどのようにすれば検証することができ、準拠していない場合に修復するには何を行う必要がありますか?
* Contoso Pharma は、北米とヨーロッパで活動する世界的な製薬会社です。
* ワークロード間でデータ暗号化を適用するために使用できる Azure サービスは何ですか?
