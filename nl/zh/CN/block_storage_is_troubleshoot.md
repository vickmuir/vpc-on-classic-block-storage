---

copyright:
  years: 2019
lastupdated: "2018-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot

subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# {{site.data.keyword.block_storage_is_short}} 故障诊断
{: #troubleshoot}

创建或管理 {{site.data.keyword.block_storage_is_short}} 时，可能会遇到问题。通常，通过执行一些简单的步骤就可以恢复。以下各部分中描述了问题、症状、可能的原因和解决方法。
{:shortdesc}

## 检索不到指定区域中的卷
{: #troubleshoot-topic-1}

对于给定区域，检索不到有关一个或多个块存储卷的信息。
{: tsSymptoms}

这可能是因为以下任一原因：

* UI 或 CLI 输出中缺少卷名和信息。
* 还有可能您尝试访问的是您所在区域之外的区域中的卷。
* 您可能尝试访问的是第 2 代卷。
{: tsCauses}

验证卷是否未从虚拟服务器实例拆离且未删除。在所有虚拟服务器实例的列表中搜索上次将卷连接到的实例：

1. 在 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/vpc){: external}中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > 计算 > 虚拟服务器实例**。

1. 从所有虚拟服务器的列表中选择虚拟服务器实例。

如果卷未按预期连接，并且未显示在卷列表中，那么可能已删除该卷。由于删除卷会完全除去其数据，因此无法将其复原。  

如果使用的是 CLI，请验证输入的用于查看卷的语法是否正确。请参阅[通过 CLI 查看所有块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。验证指定的资源组或专区是否正确。
{: tsResolve}

## 无法通过名称或标识删除卷
{: #troubleshoot-topic-2}

无法通过名称或标识删除块存储卷。
{: tsSymptoms}

卷名和标识不可接受。
{: tsCauses}

验证卷名或标识是否正确，以及卷是否未连接到虚拟服务器实例。此外，验证卷是否未处于暂挂状态。
{: tsResolve}
