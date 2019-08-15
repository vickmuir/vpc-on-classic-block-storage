---

copyright:
  years: 2019
lastupdated: "2019-07-11"

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

# 使用 UI 管理块存储卷
{: #managing-block-storage}

在 UI 中管理 {{site.data.keyword.block_storage_is_short}}。从虚拟服务器实例拆离卷，将卷从一个实例传输到另一个实例，连接先前已连接的卷，重命名卷，设置自动卷删除，手动删除卷或分配对卷的访问权。
{:shortdesc}

## 从虚拟服务器实例拆离块存储卷
{: #detach}

您可以拆离当前连接到虚拟服务器实例的块存储卷。通过拆离，可释放卷以供其他实例使用。

要拆离卷，请执行以下操作：

1. 导航至所有块存储卷的列表。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，转至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > Block Storage**。
1. 找到该卷，然后单击表行末尾的省略符 (...)。这将显示上下文菜单。
1. 在菜单中，单击**从实例拆离**。
1. 单击弹出窗口中的**拆离实例**以确认操作。

或者，可以单击所有块存储卷的列表中的单个卷，并导航至该卷的**卷详细信息**页面。在**连接的实例**下，单击虚拟服务器实例旁边的减号以从该实例拆离卷。

## 将块存储卷从一个虚拟服务器实例转移到另一个虚拟服务器实例
{: #transfer}

要将块存储卷转移到另一个虚拟服务器实例，请执行以下操作：

1. [从卷的虚拟服务器实例拆离卷](#detach)。
1. 导航至要将卷转移到的虚拟服务器实例。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，转至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 计算 > 虚拟服务器实例**。
1. 从列表中选择虚拟服务器。
1. 在“连接的存储卷”下，单击加号以添加卷。这将显示所有块存储卷。
1. 从卷列表中，选择先前拆离的卷。

## 连接先前连接的块存储卷
{: #reattach}

创建新的虚拟服务器实例时，缺省情况下会连接块存储卷。从实例拆离卷后，该卷会作为未连接卷存在，并显示在[所有块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)的列表中。您可以在块存储卷列表中将其连接到其他映像。

1. 导航至所有块存储卷的列表。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > Block Storage**。
1. 找到该卷，然后单击表行末尾的省略符 (...)。这将显示上下文菜单。
1. 在菜单中，单击**连接到实例**。
1. 选择可用的虚拟服务器实例。
1. 确认您的选择。

## 重命名块存储卷
{: #rename}

可以更改现有卷的名称以使其更富有意义。

1. 导航至所有块存储卷的列表。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，转至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > Block Storage**。
1. 找到卷，然后单击该卷的名称以转至“卷详细信息”页面。
1. 单击卷名后的“画笔”图标，然后编辑卷名。
1. 确认您的编辑。

## 删除块存储卷
{: #delete}

删除块存储卷将完全除去其数据。无法复原卷。

无法删除活动块存储卷。要删除卷，请先从虚拟服务器[拆离卷](#detach)，然后执行以下步骤：

1. 导航至所有块存储卷的列表。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，转至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 存储 > Block Storage**。
1. 找到要删除的卷，然后单击表行末尾的省略符。这将显示上下文菜单。
1. 在菜单中，单击**删除**。
1. 确认此删除操作。

## 自动删除块存储数据卷
{: #auto-delete}

通过使用“自动删除”功能，可以指定在删除块存储数据卷连接到的实例时自动删除该卷。此功能不适用于引导卷，并且缺省情况下此功能已禁用。

要对连接到实例的现有块存储卷启用自动删除，请执行以下步骤：

1. 找到卷连接到的虚拟服务器实例。在用于 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 计算 > 虚拟服务器实例**。
1. 在**连接的块存储卷**下，选择卷。
1. 在弹出菜单上，单击“自动删除”按钮以启用自动删除。
1. 确认您的选择。

或者，首先从块存储卷列表中选择卷（**存储 > Block Storage**）。

要在创建实例时在新卷上启用自动删除，请参阅[创建新实例时创建并连接块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)。

## 分配对块存储卷的访问权
{: #assign-volume-access}

通过管理员特权，您可以分配对 {{site.data.keyword.block_storage_is_short}} 服务的卷级别用户访问权。下表显示了必须在 [Identity and Access Management (IAM) UI](/docs/iam?topic=iam-account_setup#assigning-access) 中提供的信息。

|IAM 字段|操作|
|--------|-------------|
|服务|选择**基础架构服务**|
|资源类型|选择 **Block Storage for VPC**|
|卷标识|输入 [卷标识](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details)以分配对特定卷的访问权|
|选择角色|分配平台访问角色，通常为操作员|
{: caption="表 1. IAM 的信息" caption-side="top"}

有关更多信息，请参阅[分配访问权的最佳实践](/docs/iam?topic=iam-account_setup#account_setup)。有关完整的 IAM 过程（包括邀请用户加入帐户和分配 Cloud IAM 访问权），请参阅 [IAM 入门教程](/docs/iam?topic=iam-getstarted#getstarted)。

## 块存储卷状态
{: #status}

下表显示了在创建、查看或管理块存储卷时可能看到的状态。

|状态|含义|
|--------|-------------|
|可用|已成功检索到卷|
| |卷可用，并且可以连接到实例|
| |连接的卷可用于存储数据
| |引导卷可用|
|失败|卷创建失败|
| |无法检索到区域中的所有卷|
| |找不到具有指定卷标识的卷|
| |无法删除卷|
|暂挂|正在创建卷|
| |卷正在连接到实例|
|暂挂待删除|正在删除卷|
{: caption="表 2. Block Storage 状态" caption-side="top"}

您希望使用 CLI 来管理块存储卷？有关信息，请参阅[管理块存储卷 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)。
{: tip}

## 后续步骤
{: #next-step-managing-block-storage}

可以[创建其他卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)。

对于现有块存储卷发生的问题，您可能可以自行进行故障诊断并解决问题。有关更多信息，请参阅[有关块存储器的故障诊断](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)。
