---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# {{site.data.keyword.block_storage_is_short}} 容量和性能
{: #capacity-performance}

选择工作负载的最佳块存储卷大小和性能级别非常重要。通过 UI 或 CLI 供应 {{site.data.keyword.block_storage_is_short}} 卷时，可以选择卷容量和性能级别。
{:shortdesc}

## 容量
{: #block-storage-vpc-capacity}

可以为每个块存储器数据卷指定 10 GB 到 2000 GB (2 TB) 容量（以 1 GB 为增量）。在选择 [IOPS 概要文件](#iops-profiles)时，确定卷的总容量。引导卷为 100 GB。

## IOPS 概要文件
{: #iops-profiles}

供应 {{site.data.keyword.block_storage_is_short}} 卷时，可指定最符合您存储需求的 [IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)。概要文件可作为三个预定义 IOPS 层提供，也可作为定制 IOPS 提供。[IOPS 层](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)可为最高 2 TB 容量的卷提供保证的 IOPS/GB 性能。您还可以指定[定制 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) 概要文件，并定义某一范围内的卷容量和 IOPS。使用 {{site.data.keyword.cloud_notm}} 控制台、CLI 或 API 来指定概要文件。

## 块大小如何影响性能
{: #how-block-size-affects-performance}

IOPS 基于 16 KB 块大小，其中读写随机工作负载的比例为 50/50。一个 16 KB 块相当于对卷执行一次写操作。基线吞吐量由 IOPS 乘以 16 KB 块大小来确定。指定的 IOPS 越高，吞吐量越大。块存储卷的最大吞吐量为 750 MB/秒。

为应用程序选择的块大小会直接影响存储性能。如果块大小小于 16 KB，那么会在达到吞吐量限制之前，先达到 IOPS 限制。相反，如果块大小大于 16 KB，那么会在达到 IOPS 限制之前，先达到吞吐量限制。下表提供了块大小和 IOPS 如何影响吞吐量的一些示例，计算的平均 I/O 大小 x IOPS = 吞吐量（MB/秒）。

|块大小 (KB)|IOPS|吞吐量（MB/秒）|
|-----------------|------|-------------------|
|4（Linux 的典型值）|1,000|4|
|8（Oracle 的典型值）|1,000|8|
|16|1,000|16|
|32（SQL Server 的典型值）|500|16|
|64|250|16|
|128|128|16|
{: caption="表 1. 块大小和 IOPS 如何影响吞吐量的示例" caption-side="top"}
