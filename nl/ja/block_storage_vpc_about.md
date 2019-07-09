---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS, HPCS, Key Protect

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Block Storage for VPC について
{: #block-storage-about}
[comment]: # (リンクされたヘルプ・トピック)

{{site.data.keyword.block_storage_is_full}} (VPC) は、ハイパーバイザーにマウントされた高性能データ・ストレージを、{{site.data.keyword.vpc_full}} (VPC) 内でプロビジョンできる仮想サーバー・インスタンス (インスタンス) に提供しています。VPC インフラストラクチャーは、複数の地域とゾーンにわたる迅速なスケーリングや、追加のパフォーマンスとセキュリティーを提供しています。{{site.data.keyword.vpc_short}} について詳しくは、[Virtual Private Cloud について](/docs/vpc-on-classic?topic=vpc-on-classic-about)を参照してください。
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} は、1 次ブート・ボリュームと 2 次データ・ボリュームを提供します。ブート・ボリュームは、インスタンスのプロビジョニング中に自動的に作成されて接続されます。データ・ボリュームは、同じくインスタンスのプロビジョン中に作成して接続したり、スタンドアロン・ボリュームとして作成して後でインスタンスに接続したりできます。データを保護するために、独自の暗号鍵を使用するか、IBM 管理の暗号化を選択することができます。[IOPS ティア・プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)を使用すると、ボリュームに関するパフォーマンスの事前定義済みのレベルを指定できます。あるいは、[カスタム IOPS プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)を選択して、独自のボリューム容量と IOPS レベルを定義できます。

## Block storage for VPC のボリューム
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} は、ブート・ボリュームまたはデータ・ボリュームとしてインスタンスに接続できる、ブロック・レベルのデータ・ストレージ・ボリュームを提供します。地域あたり最大 750 個のブロック・ストレージ・ボリュームを構成できます。容量を追加するために、複数のブロック・ストレージ・データ・ボリュームを単一インスタンスに接続できます。インスタンスに接続できるボリュームの数は、そのインスタンスに含まれている vCPU の数に応じて異なります。詳しくは、[ボリューム接続の制限](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)を参照してください。

### ブート・ボリューム
{: #block-storage-vpc-boot-volumes}

インスタンスを作成する際に、100 GB のブート・ボリュームが自動的に作成され、インスタンスに接続されます。ブート・ボリュームの最大 IOPS は 3,000 IOPS です。ブート・ボリュームの暗号化には、[独自の暗号鍵](#about-customer-managed-encrytion)を使用したりデフォルトの[プロバイダー管理の暗号化](#about-provider-managed-encryption)を使用したりできます。ブート・ボリュームは手動で切り離すことも削除することもできませんが、インスタンスを削除するとブート・ボリュームも削除されます。

### 2 次データ・ボリューム
{: #secondary-data-volumes}

ブロック・ストレージ・データ・ボリュームは、合計容量が 10 GB から 2000 GB までの範囲の 2 次ボリュームです。データ・ボリュームの最大 IOPS は、選択したボリューム・サイズと IOPS ティア・プロファイルに基づいて異なります。例えば、1 TB までの汎用ボリュームの最大 IOPS は 3,000 IOPS です。詳しくは、[階層化 IOPS プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)を参照してください。

データ・ボリュームは、スタンドアロン・ボリュームとして作成するか、インスタンスのプロビジョン時に作成します。スタンドアロン・ボリュームは、手動でインスタンスに接続するまで未接続の状態になります。インスタンスのプロビジョニングの一部としてデータ・ボリュームを作成する場合は、そのボリュームはインスタンスに自動的に接続されます。  

[いくつかの制限](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)の中で、ブロック・ストレージ・データ・ボリュームを領域内の使用可能な任意のインスタンスに接続できます。デフォルトでは、これらのボリュームはインスタンスの削除時に切り離されます。デフォルトで切り離される場合、仮想サーバー・インスタンスのライフサイクルを超えてデータを保持できます。ボリュームとインスタンスとの関連付けのみが削除されます。データ・ボリュームは、切り離された後に手動で削除するか、またはボリュームを作成する際に、インスタンスの削除時に[自動的にデタッチされて削除](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete)されるように指定することができます。

デフォルトでは、データ・ボリュームは IBM 管理の暗号化を使用して暗号化されます。オプションで、[独自の暗号鍵](#about-customer-managed-encrytion)を使用してデータ・ボリュームを暗号化できます。

## 保存されたデータの暗号化
{: #encryption}

{{site.data.keyword.cloud_notm}} はセキュリティーのニーズを真剣に受け止め、安全を維持するためにデータの暗号化機能が重要であることを理解しています。スタンドアロン・ボリュームを作成する際や、インスタンス作成の一環としてボリュームを作成する際に、IBM プロバイダー管理の暗号化を使用してデータを保護するか、独自の暗号鍵を使用するかを選択できます。  

### プロバイダー管理の暗号化
{: #about-provider-managed-encryption}

デフォルトでは、すべてのブート・ボリュームとデータ・ボリュームは、IBM プロバイダー管理の暗号化を使用して暗号化されます。このサービスに対する追加コストや、パフォーマンスへの影響はありません。プロバイダー管理の暗号化は、以下の業界標準プロトコルを使用します。

* AES-256 暗号化
* 鍵は、Key Management Interoperability Protocol (KMIP) を使用して社内で管理されます。
* ストレージは、連邦情報処理標準 (FIPS) Publication 140-2、Federal Information Security Management Act (FISMA)、医療保険の積算と責任に関する法律 (HIPAA) に対応しています。 ストレージは、Payment Card Industry (PCI)、Basel II, California Security Breach Information Act (SB 1386)、および EU Data Protection Directive 95/46/EC コンプライアンスにも対応しています。

### お客様管理の暗号化
{: #about-customer-managed-encrytion}

独自の暗号鍵を使用して、ブロック・ストレージ・ボリュームを暗号化できます。データ・ボリュームの場合、ボリュームの作成時にお客様管理の暗号化を指定します。ブート・ボリュームの場合、インスタンスの作成時にブート・ボリューム・プロパティーを編集して、お客様管理の暗号化を指定できます。手順については、[お客様管理の暗号化を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)を参照してください。

お客様管理の暗号化の使用時には、暗号鍵が鍵管理サービス ({{site.data.keyword.keymanagementservicelong_notm}} または {{site.data.keyword.hscrypto}}) にアップロードされます。VPC インフラストラクチャーは、あらかじめ構成済みの鍵管理サービス・インスタンス内で鍵を見つけ、ボリュームを暗号化します。前提条件と一回限りのセットアップの手順については、[お客様管理の暗号化を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)を参照してください。

仮想サーバー・インスタンスのプロビジョニング時に、ボリュームに対してお客様管理の暗号化を作成することについて詳しくは、[Customer managed encryption for block storage](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys) を参照してください。

## 関連情報

VPC でのインスタンスの作成と管理について詳しくは、[Virtual Servers for VPC について](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud)を参照してください。

Block Storage for VPC の作成を開始するには、[ブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage)を参照してください。

{{site.data.keyword.block_storage_is_short}} は VPC に固有の機能を提供しており、クラシック・インフラストラクチャーのストレージとは互換性がありません。クラシック・インフラストラクチャー上の {{site.data.keyword.blockstoragefull}} に関心がある場合は、[{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About) を参照してください。
{:note}
