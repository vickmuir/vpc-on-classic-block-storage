---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# Block Storage for VPC 常见问题
{: #block-storage-vpc-faq}

## 如何为实例分配存储器？
{: faq}

创建虚拟服务器实例时，可以[创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)，该卷将连接到该实例。您还可以[创建独立卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol)，日后将其连接到实例。

## 有多少实例可以共享供应的块存储卷？
{: faq}

块存储卷一次只能连接到一个实例。多个实例不能共享同一卷。

## 可以将多少个块存储辅助（数据）卷连接到实例？
{: faq}

vCPU 少于 4 个的实例可以最多连接 4 个块存储辅助卷。

vCPU 等于或多于 4 个的实例可以最多连接 12 个块存储辅助卷。

## 供应 IOPS 时，是按实例还是按卷强制实施分配的 IOPS？
{: faq}

IOPS 在卷级别强制实施。

## 如何度量 IOPS？
{: faq}

IOPS 基于 16 KB 块的负载概要文件进行度量，其中随机读写操作各占 50%。不同于此概要文件的工作负载可能会遇到性能降低问题。

## 什么是 IOPS 概要文件？
{: faq}

IOPS 概要文件为各种容量的卷定义 IOPS/GB 性能。有三个预定义的 [IOPS 层](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，可以根据工作负载需求选择相应的 IOPS 层来提供保证的 IOPS 性能。您还可以定义[定制 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，并为选择的卷大小指定 IOPS 范围。预定义的 IOPS 层不满足明确定义的性能需求时，定制 IOPS 是不错的选择。

## 可以预期的数据卷最大 IOPS 是多少？
{: faq}

数据卷的最大 IOPS 根据选择的卷大小和 IOPS 层概要文件而变化。例如，最高 1 TB 通用卷的最大 IOPS 为 3,000 IOPS。有关信息，请参阅[分层 IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)。如果选择[定制 IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，还应针对给定卷大小，定义最小值和最大值范围。

## 如果在度量性能时使用更小的块大小，会发生什么情况？
{: faq}

使用更小的块大小时，仍然可以获得最大 IOPS，但是吞吐量会下降。例如，下面是具有 6000 IOPS 的卷针对各种不同块大小的吞吐量：

* 16 KB * 6000 IOPS == 约 93.75 MB/秒
* 8 KB * 6000 IOPS == 约 46.88 MB/秒
* 4 KB * 6000 IOPS == 约 23.44 MB/秒

## 将按使用量收费吗？是否有配额限制？
{: faq}

有关如何计费的更多信息，请参阅 [Block Storage for VPC 的定价](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing)。某些限制适用。有关 {{site.data.keyword.cloud}} Virtual Private Cloud 以及其中可用资源的配额和限制的更多信息，请参阅[配额](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas)。

## 创建卷后，日后可以增大其容量吗?
{: faq}

不能，不能增大卷的容量。建议您在供应块存储卷之前，估算足够的容量以满足预测的增长。

## 卷需要预热才能达到所需吞吐量吗？
{: faq}

您不必对卷进行预热。供应卷后，可立即看到指定的吞吐量。

## 可以创建加密卷吗？
{: faq}

所有块存储卷都会通过 IBM 管理的加密（缺省值）进行加密，或者使用您自己的加密密钥通过 Key Protect 服务进行加密。有关信息，请参阅[创建使用客户管理的加密的块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。

## 如何判断卷的加密类型？
{: faq}

在 UI 中，查看所有块存储卷的列表时，“加密”列会指示提供者管理的加密或客户管理的加密。

要通过 CLI 显示卷的属性，请输入：

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## 我的数据有多安全？
{: faq}

所有块存储卷都会通过 IBM 管理的加密或使用您自己的加密密钥进行静态加密。IBM 管理的密钥在 Consul 支持的块存储器保险库中生成并安全地存储在其中，然后由系统进行维护。客户管理的密钥使用 IBM Key Protect 服务安全地进行管理。

## 对于用于灾难恢复的数据备份，我应该做些什么？
{: faq}

Block Storage for VPC 可保护您所在区域的冗余故障专区中的数据。此外，我们鼓励您独立备份数据。您还可以考虑使用 [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started)，此产品提供了灾难恢复功能，例如卷克隆、快照和复制。

## 可以供应多少个卷？
{: faq}

每个区域最多可以供应 1,000 个块存储卷。

## 应该使用什么策略来管理卷？
{: faq}

根据预期增长确定所需的容量。卷供应后，即无法扩展卷大小。但是，您可以根据需要创建新卷。此外，如果您有明确定义的性能需求，那么可考虑选择[定制 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，这可根据卷大小提供特定范围的 IOPS。

## 如何创建虚拟服务器实例的引导磁盘，引导磁盘与映像文件是什么关系？
{: faq}

引导磁盘（也称为引导卷）是在供应虚拟服务器实例时创建的。实例的引导磁盘是虚拟机映像的克隆映像。删除引导卷连接的实例时，将同时删除引导卷。

## 防火墙或安全组会影响性能吗？
{: faq}

作为最佳实践，建议在绕过防火墙的 VLAN 上运行存储流量。通过软件防火墙运行存储流量会延长等待时间，并对存储器性能产生负面影响。

## 何时可以删除块存储数据卷？
{: faq}

仅当块存储数据卷未连接到虚拟服务器实例时，才能将其删除。在删除卷之前，请[拆离卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)。删除实例时，会拆离并删除引导卷。

## 删除块存储数据卷时，数据会发生什么情况？
{: faq}

删除块存储数据卷时，将除去指向该卷上数据的所有指针，因此数据会变得完全不可访问。如果日后将该物理存储器重新供应给其他帐户，那么会分配一组新的指针。此新帐户无法访问该物理存储器上原先可能存在的任何数据；新的一组指针全部显示为 0。将新数据写入卷时，将覆盖任何不可访问的数据。

## 预期块存储器的性能等待时间有多长？
{: faq}

存储器中的目标等待时间短于 1 毫秒。块存储器是连接到共享网络上的计算实例，因此确切的性能等待时间将取决于给定时间范围内的网络流量。

## 可以在多专区集群中设置共享存储器吗？
{: faq}

在 IBM Cloud 中，存储选项已本地化为可用性专区。我们建议不要跨多个专区管理共享存储器。

如果必须跨多个专区和区域共享数据，请改为使用 IBM Cloud 数据经典服务选项，例如 {{site.data.keyword.cos_full}} 或 {{site.data.keyword.cloudantfull}}。

## 我在经典基础架构上具有卷。可以将这些卷移植到 VPC 吗？
{: faq}

不能。VPC 提供了对多专区区域中新可用性专区的访问权。计算、网络和存储资源专门设计为在 VPC 中运行。
