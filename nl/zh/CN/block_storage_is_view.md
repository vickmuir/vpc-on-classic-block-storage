---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# 查看块存储卷详细信息
{: #viewing-block-storage}

查看有关块存储卷的详细信息或有关所有卷的摘要信息。

## 查看有关所有块存储卷的信息
{: #viewvols}

导航至块存储卷的列表。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，转至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > Block Storage for VPC 卷**。

缺省情况下，会显示区域中所有资源组的块存储卷。在所有**块存储卷**的列表中，您将看到以下信息。

|字段|描述|
|-------|-------------|
|状态|卷的状态，可充当所有行的缺省过滤器。有关卷状态的信息，请参阅[块存储卷状态](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status)。|
|名称|单击卷名可查看各个卷的详细信息。|
|资源组|设置 VPC 时定义的资源组。资源组管理对资源的访问权，但不影响计费或监视功能。|
|位置|区域中的可用性专区，从 VPC 继承（例如，美国南部 1）。|
|大小|指定的卷大小（以 GB 为单位）。|
|最大 IOPS|卷上可用的最大 IOPS，由指定的通用 IOPS 层或定制 IOPS 值进行定义。|
|连接类型|数据（表示连接到实例的辅助卷）、引导（表示作为引导卷连接）或空白（表示未连接的卷）。|
|加密|提供者管理或[客户管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。|
|操作 (...)|单击省略符可显示菜单，其中包含可以执行的特定于上下文的操作。例如，未连接的可用卷将具有用于连接到实例或删除卷的菜单选项。|
{: caption="表 1. 有关所有卷的详细信息" caption-side="top"}

缺省情况下，所有块存储卷的列表中会显示 10 个卷。通过单击向下箭头可更改此缺省值，使列表增大到显示 20 或 50 个卷。使用右下角的箭头可导航至下一页，也可以返回上一页。

## 查看有关块存储卷的详细信息
{: #view-vol-details}

要查看有关块存储卷的详细信息，请导航至所有块存储卷的列表，然后选择卷。对于单个卷，您将看到以下信息。

|字段|描述|
|-------|-------------|
|名称|创建卷时指定的卷名。单击“画笔”图标可编辑卷名。|
|资源组|设置 VPC 时定义的资源组。资源组管理对资源的访问权，但不影响计费或监视功能。|
|连接类型|数据（表示连接到实例的辅助卷）、引导（表示作为引导卷连接）或空白（表示未连接的卷）。|
|标识|系统生成的卷标识。|
|创建时间|创建卷时系统生成的日期。|
|位置|区域中的可用性专区。|
|大小|指定的卷大小。|
|概要文件|IOPS 层或定制 IOPS 概要文件。|
|最大 IOPS|预定义 IOPS 层的最大 IOPS 值或为定制 IOPS 指定的值。|
|吞吐量|磁盘可交付的性能，以千兆位/秒 (Gbps) 为单位进行度量。根据卷概要文件，吞吐量的计算公式为 IOPS 量 * 16K 块大小。|
|加密|提供者管理或客户管理。|
{: caption="表 1. 卷详细信息" caption-side="top"}

连接到虚拟服务器实例的卷会显示在**卷详细信息**页面上**连接的实例**下。您还可以[将卷连接到实例](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)。

对于连接到实例的卷，还可以导航至有关实例的信息，然后返回到所有块存储卷的列表。

## 在实例详细信息中查看连接的块存储卷详细信息

可以在**虚拟服务器实例详细信息**页面中查看有关连接的块存储卷的信息：

1. 在 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，转至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 计算 > Virtual Server for VPC 实例**，然后选择实例。
1. 在**连接的块存储卷**下，单击卷名以转至卷详细信息页面。

您希望使用 CLI 来查看块存储卷？有关信息，请参阅[查看块存储卷 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli)。
{: tip}

## 后续步骤
{: #next-step-viewing-block-storage}

创建更多卷或管理现有块存储卷。

* [在 IBM Cloud 控制台中创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [使用 UI 管理块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
