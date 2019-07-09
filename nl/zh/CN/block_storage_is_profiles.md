---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}


# 概要文件
{: #block-storage-profiles}

使用 {{site.data.keyword.cloud_notm}} 控制台、CLI 或 API 来供应 {{site.data.keyword.block_storage_is_short}} 辅助卷时，可指定最能满足存储需求的 IOPS 概要文件。概要文件可作为三个预定义 IOPS 层提供，也可作为定制 IOPS 提供。IOPS 层可为最高 2 TB 容量的卷提供保证的 IOPS/GB 性能。您还可以指定定制 IOPS 概要文件，并定义某一范围内的卷容量和 IOPS。

## 分层 IOPS 概要文件
{: #tiers}

块存储器提供了三个预定义的 IOPS 层，您可以选择某个 IOPS 层以指定计算工作负载的最佳性能，并避免瓶颈。您可以为可用性专区中的卷供应保证的 IOPS，如下表中所述：

|IOPS 层|工作负载|卷大小|最大 IOPS|
|-----------|----------|-------------|----------|
|3 IOPS/GB|通用工作负载 - 用于为 Web 应用程序托管小型数据库或为系统管理程序存储虚拟机磁盘映像的工作负载|10 GB 到 1 TB|最高 3,000 IOPS|
| | |高于 1 TB 到 2 TB|3 IOPS/GB，最高 6,000 IOPS|
|5 IOPS/GB|高 I/O 密集型工作负载 - 以活动数据占很大百分比为特征的工作负载，例如事务性和其他性能敏感型数据库|10 GB 到 600 GB|最高 3,000 IOPS|
| | |高于 600 GB 到 2 TB|5 IOPS/GB，最高 10,000 IOPS|
|10 IOPS/GB|高要求存储工作负载 - 由 NoSQL 数据库创建的数据密集型工作负载，处理用于视频、机器学习和分析的数据|10 GB 到 300 GB|最高 3,000 IOPS|
| | |高于 300 GB 到 2 TB|10 IOPS/GB，最高 20,000 IOPS|
{: caption="表 1. IOPS 层和性能" caption-side="top"}

所有块存储器 IOPS 层的最大吞吐量为 750 MB/秒（基于 16K 块大小）

## 定制 IOPS 概要文件
{: #custom}

预定义的 IOPS 层不满足明确定义的性能需求时，定制 IOPS 是不错的选择。您可以通过为卷指定其卷大小范围内的总 IOPS 来定制 IOPS。可以为卷供应 100 IOPS 到 20,000 IOPS。

下表显示了基于卷大小的可用 IOPS 范围。

|卷大小 (GB)|IOPS 范围|
|-------------|--------------|
|10 - 39|100 - 1,000|
|40 - 79|100 - 2,000|
|80 - 99|100 - 4,000|
|100 - 499|100 - 6,000|
|500 - 999|100 - 10,000|
|1,000 - 1,999|100 - 20,000|
{: caption="表 2. 基于卷大小的可用 IOPS" caption-side="top"}

## 虚拟服务器概要文件与存储器概要文件的关系
{: #vsi-profiles-relate-to-storage}

虚拟服务器概要文件是 vCPU 和 RAM 的组合，可以快速对其进行实例化以启动虚拟服务器实例。您可根据工作负载需求，从[三个概要文件系列](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)中进行选择。这些需求的范围从常见工作负载到 CPU 密集型或内存密集型工作负载。  

与此类似，存储概要文件（IOPS 层或定制）为辅助卷提供一系列容量和性能。缺省情况下，创建虚拟服务器实例时，将创建 100 GB 主引导卷。您还可以创建并连接辅助卷。  
在实例创建过程中创建辅助数据卷时，可选择最符合计算工作负载存储需求的存储器概要文件。通常，随着计算需求的增加，会需要更高的 IOPS 性能。下表显示了这一关系。

|IOPS 层存储概要文件|虚拟服务器概要文件|
|-----------------|------------------------|
|3 IOPS/GB|[均衡](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced)（对于常见工作负载）|
|5 IOPS/GB|[计算](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute)（对于密集型 CPU 需求）|
|10 IOPS/GB|[内存](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory)（对于内存密集型工作负载）|

## 查看 IOPS 概要文件
{: #view-iops-profiles}

可以使用 {{site.data.keyword.cloud_notm}} 控制台、CLI 或 API 来查看可用的 IOPS 概要文件。

### 使用 IBM Cloud 控制台
{: using-console-iops-profile}

 [在 {{site.data.keyword.cloud_notm}} 控制台中创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)时，请从下拉菜单中选择**层**。

 或者，选择**定制**，然后选择该卷大小范围内的 IOPS 值。单击“存储器大小”链接以查看大小和 IOPS 范围的表。

 ### 使用 CLI
 {: using-cli-iops-profiles}

 要使用 CLI 查看可用概要文件的列表，请运行以下命令：
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### 使用 API
{: using-api-iops-profiles}

以下 cURL API 请求检索所有卷概要文件。

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## 相关信息

有关 {{site.data.keyword.vsi_is_short}} 的均衡、计算和内存概要文件的信息，请参阅[概要文件](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)。
