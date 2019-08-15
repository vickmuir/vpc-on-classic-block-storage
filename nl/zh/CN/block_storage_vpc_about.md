---

copyright:
  years: 2019
lastupdated: "2019-07-22"

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

# 有关 {{site.data.keyword.block_storage_is_short}}
{: #block-storage-about}
[comment]: # (链接的帮助主题)

{{site.data.keyword.block_storage_is_full}} (VPC) 为虚拟服务器实例提供了通过系统管理程序安装的高性能数据存储器，您可以在 {{site.data.keyword.vpc_full}} (VPC) 中供应这些实例。通过 VPC 基础架构，可跨多个区域和专区进行快速缩放，并实现额外的性能和安全性。有关 {{site.data.keyword.vpc_short}} 的更多信息，请参阅[关于 Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)。
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} 提供主引导卷和辅助数据卷。在实例供应期间，会自动创建并连接引导卷。还可以在实例供应期间创建和连接数据卷，或者将卷创建为独立卷，日后可以将这些卷连接到实例。要保护数据，您可以使用自己的加密密钥，也可以选择 IBM 管理的加密。通过 [IOPS 层概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，可以为卷指定预定义的性能级别。或者，可以选择[定制 IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，然后定义您自己的卷容量和 IOPS 级别。

## Block Storage for VPC 卷
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} 提供块级别数据存储卷，这些卷可以作为引导卷或作为数据卷连接到实例。每个区域最多可以配置 750 个块存储卷。您可以将多个块存储数据卷连接到单个实例，以获取额外的容量。可以连接到实例的卷数取决于该实例包含的 vCPU 数。有关更多信息，请参阅[卷连接限制](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)。

### 引导卷
{: #block-storage-vpc-boot-volumes}

创建实例时，会自动创建 100 GB 引导卷并将其连接到实例。引导卷的最大 IOPS 为 3,000 IOPS。可以使用[您自己的加密密钥](#about-customer-managed-encrytion)来加密引导卷，也可以使用缺省[提供者管理的加密](#about-provider-managed-encryption)。无法手动拆离和删除引导卷，但在删除实例时会将其删除。

### 辅助数据卷
{: #secondary-data-volumes}

块存储数据卷是辅助卷，总容量范围为 10 GB 到 2000 GB。数据卷的最大 IOPS 根据选择的卷大小和 IOPS 层概要文件而变化。例如，最高 1 TB 通用卷的最大 IOPS 为 3,000 IOPS。有关更多信息，请参阅[分层 IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)。

您可以将数据卷创建为独立卷，也可以在供应实例时创建数据卷。独立卷始终处于未连接状态，直到将卷连接到实例为止。在实例供应过程中创建数据卷时，卷会自动连接到实例。  

块存储数据卷可以连接到区域内的任何可用实例，但存在[特定限制](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)。缺省情况下，删除实例时，会拆离这些卷。缺省情况下，拆离操作允许数据的持久存储时间长于虚拟服务器实例生命周期。拆离操作仅除去卷与实例的关联。可以在拆离数据卷后手动删除这些卷，或者在创建卷时，可以指定在删除实例时[自动拆离并删除](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete)这些卷。

缺省情况下，数据卷会使用 IBM 管理的加密进行加密。（可选）可以使用[您自己的加密密钥](#about-customer-managed-encrytion)来加密数据卷。

## 静态数据的 Block Storage 加密
{: #encryption}

{{site.data.keyword.cloud_notm}} 十分重视安全需求，并认识到能够加密数据来确保数据安全的重要性。创建独立卷或在实例创建过程中创建卷时，可以选择使用 IBM 提供者管理的加密或使用您自己的加密密钥来保护数据。  

### 提供者管理的加密
{: #about-provider-managed-encryption}

缺省情况下，所有引导卷和数据卷均使用 IBM 提供者管理的加密进行加密。此服务没有额外成本，也不会影响性能。提供者管理的加密使用以下业界标准协议：

* AES-256 加密
* 密钥通过密钥管理互操作性协议 (KMIP) 内部进行管理
* 存储器已通过美国联邦信息处理标准 (FIPS) 出版物 140-2 的验证，符合《联邦信息安全管理法案》(FISMA) 和《健康保险可移植性和责任法案》(HIPAA)。此外，存储器还通过了支付卡行业 (PCI) 标准的验证，符合《新巴塞尔协议》、《加利福尼亚州违反安全信息法》(SB 1386) 和《欧盟数据保护指令 (95/46/EC)》。

### 客户管理的加密
{: #about-customer-managed-encrytion}

您可以使用自己的加密密钥对块存储卷进行加密。对于数据卷，可在创建卷时指定客户管理的加密。对于引导卷，可以在创建实例期间，通过编辑引导卷属性来指定客户管理的加密。有关过程，请参阅[创建使用客户管理的加密的块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。

使用客户管理的加密时，加密密钥会上传到密钥管理服务（{{site.data.keyword.keymanagementservicelong_notm}} 或 {{site.data.keyword.hscrypto}}）。VPC 基础架构在密钥管理服务实例中找到预先配置的密钥，然后对卷进行加密。有关先决条件和一次性设置过程，请参阅[创建使用客户管理的加密的块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。

有关在虚拟服务器实例供应期间为卷创建客户管理的加密的更多信息，请参阅[对块存储器进行客户管理的加密](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys)。

## 相关信息

有关在 VPC 中创建和管理实例的更多信息，请参阅[关于 Virtual Server for VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud)。

要开始为 VPC 创建块存储器，请参阅[创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage)。

{{site.data.keyword.block_storage_is_short}} 提供的功能仅适用于 VPC，与经典基础架构存储器不兼容。如果您对经典基础架构上的 {{site.data.keyword.blockstoragefull}} 感兴趣，请参阅 [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About)。
{:note}
