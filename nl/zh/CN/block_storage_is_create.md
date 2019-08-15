---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# 在 {{site.data.keyword.cloud_notm}} 控制台中创建块存储卷
{: #creating-block-storage}
[comment]: # (链接的帮助主题)

您可以在创建虚拟服务器实例时创建 {{site.data.keyword.block_storage_is_short}} 卷，或者创建独立卷，以便日后连接到实例。
{:shortdesc}

开始之前，请确保已[创建 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

## 创建新实例时创建并连接块存储卷
{: #create-from-vsi}

1. 创建实例。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 计算 > 虚拟服务器实例 > 新建实例**。
1. [配置虚拟服务器实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers)。在**连接的块存储卷**下，选择**新建块存储卷**。
1. 输入下表中描述的信息。完成后，单击**创建卷**。

|字段|值|
|-------|-------|
|名称|为卷指定有意义的名称，例如用于描述计算或工作负载功能的名称。可以输入字母和数字字符的组合，并且日后可根据需要编辑名称。|
|概要文件|选择[层](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，然后从 IOPS 列表中选择所需的性能级别。如果预定义的 IOPS 层不能满足您的性能需求，请选择[定制](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，然后选择该卷大小范围内的 IOPS 值。单击**存储器大小**链接以查看大小和 IOPS 范围的表。|
|自动删除|启用此功能可在删除连接的虚拟服务器实例时自动删除此卷。可稍后在虚拟服务器详细信息页面上更改此设置。|
|IOPS|对于“分层概要文件”，选择 3、5 或 10 IOPS/GB|
|大小|输入卷大小（以 GB 为单位）。卷大小可以介于 10 GB 到 2 TB 之间。|
|加密|缺省情况下，所有卷上都启用了使用 IBM 管理的密钥的加密。您还可以选择**客户管理**，并使用您自己的加密密钥。有关设置客户管理的加密的先决条件和步骤，请参阅[创建使用客户管理的加密的块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。|
{: caption="表 1. 供应实例时指定的块存储卷值" caption-side="top"}

这将创建块存储卷，并将其连接到虚拟服务器实例。在实例详细信息页面上，**连接的块存储卷**列表将更新为显示新卷。

块存储卷一次只能连接到一个虚拟服务器。在块存储器卷摘要页面上，可以通过在**连接的实例**下选择虚拟服务器实例名称，查看有关该实例的详细信息。

## 创建独立块存储卷
{: #create-standalone-vol}

您可以独立于虚拟服务器供应来创建块存储卷，并且日后将卷连接到实例。

1. 在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > 块存储卷**，然后选择**新建卷**。
1. 输入下表中的信息以定义新的块存储卷。
1. 完成后，单击**创建卷**。您将返回到“块存储卷”页面，其中一条消息指示正在创建卷。创建了卷后，将显示另一条消息。
1. 要查看新卷的详细信息，请选择后一条消息中的**查看资源**链接，以导航至“卷详细信息”页面。

|字段|值|
|-------|-------|
|名称|为卷指定有意义的名称。例如，提供用于描述计算或工作负载功能的名称。最多可以输入 40 个字母数字字符，并且日后可编辑名称。|
|资源组|指定资源组。资源组帮助组织帐户资源，以进行访问控制和计费。有关设置资源组的信息，请参阅[在资源组中组织资源的最佳实践](/docs/resources?topic=resources-bp_resourcegroups#setuprgs)。|
|标记|指定用于组织资源的标记。标记是您为资源分配的标签，用于对资源列表中的资源进行轻松过滤。有关标记的信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。|
|位置|区域中的可用性专区，从 VPC 继承（例如，美国南部 1）。|
|大小|输入卷大小（以 GB 为单位）。卷大小可以介于 10 GB 到 2 TB 之间。|
|IOPS|选择 [IOPS 层](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，然后选择具有所需性能级别的磁贴。|
|定制|根据指定的卷大小，选择该卷大小范围内的 IOPS 值。单击**存储器大小**链接以查看大小和 IOPS 范围的表。有关更多信息，请参阅[定制 IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)。|
|加密|缺省情况下，所有卷上都启用了使用 IBM 管理的密钥的加密。要使用您自己的加密密钥，请选择“客户管理的加密”选项。有关信息，请参阅[创建使用客户管理的加密的块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。|
{: caption="表 2. 用于定义块存储卷的值" caption-side="top"}

您希望使用 CLI 来创建块存储卷？有关信息，请参[使用 CLI 创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)。
{: tip}

## 后续步骤
{: #next-step-creating-block-storage}

刷新“块存储卷”页面时，新卷将显示在卷列表的顶部。如果已成功创建卷，其状态显示为“可用”。对于独立卷，“连接类型”列为空白 (-)。表行末尾的“操作”菜单 (...) 提供了[将块存储卷连接到实例](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)的链接。

您可以继续创建更多块存储卷或管理现有卷。

* [查看有关块存储卷的详细信息](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [从虚拟服务器实例拆离卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [删除块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
