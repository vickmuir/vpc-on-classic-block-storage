---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, block storage volume, volume, volume attachment, virtual server instance, instance

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

# 使用 UI 连接块存储卷
{: #attaching-block-storage}

在 UI 中为虚拟服务器实例创建 {{site.data.keyword.block_storage_is_short}} 卷时，缺省情况下，卷会连接到实例。拆离卷后，卷会作为未连接的卷存在，日后可以重新连接该卷。这些可用卷会显示在[所有块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)的列表中。您可以在所有块存储卷的列表中，或者在查看有关特定实例的详细信息时，将卷连接到其他实例。
{:shortdesc}

## 卷连接限制
{: #vol-attach-limits}

虽然一次只能将一个块存储卷连接到虚拟服务器实例，但可以将多个不同的块存储卷连接到单个实例，不过有以下限制：

* 虚拟 CPU 少于 4 个的实例可以连接引导卷以及最多 4 个块存储辅助卷。
* 虚拟 CPU 等于或多于 4 个的实例可以连接引导卷以及最多 12 个块存储辅助卷。

## 将块存储卷连接到虚拟服务器实例
{: #attach}

在所有块存储卷的列表中，执行以下步骤。

1. 在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > Block Storage**。
1. 在卷列表中，单击未连接的可用卷所在行末尾的省略符。这将显示特定于上下文的操作菜单。
1. 选择**连接到实例**。
1. 从可用资源列表中选择计算资源（虚拟服务器实例），然后单击**连接**。
1. 这将在卷详细信息页面上显示消息，指示卷正在连接到映像。完成后，映像名称将显示在**连接的实例**下。

您还可以在虚拟服务器实例详细信息页面中连接块存储卷。

1. 在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 计算 > 虚拟服务器实例**。
1. 从所有虚拟服务器实例的列表中选择实例。如果该实例连接了任何块存储卷，那么将在**连接的块存储卷**下看到这些卷。
1. 选择**连接卷**。
1. 从可用资源列表中选择卷，然后单击**连接**。这将在实例详细信息页面上显示消息，指示正在连接卷。完成后，**连接的块存储卷**列表将更新为包含新卷。

您还可以使用 CLI 手动连接块存储卷。有关信息，请参阅[连接块存储卷 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。
{: tip}

## 后续步骤
{: #next-step-attaching-block-storage}

创建其他卷并管理现有卷。请参阅以下信息。

* [在 IBM Cloud 控制台中创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [使用 UI 管理块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
