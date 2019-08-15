---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, getting started, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

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
{:shortdesc: .shortdesc}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# 开始使用 {{site.data.keyword.block_storage_is_short}}
{: #getting-started}

本教程可帮助您开始在 Virtual Private Cloud 上创建 {{site.data.keyword.block_storage_is_short}} 卷。
{: .shortdesc}

## 开始之前
{: #block-storage-before-you-begin}

首先，请查看可帮助您实现上述操作的内容。您不熟悉 {{site.data.keyword.cloud}} 和 {{site.data.keyword.block_storage_is_short}}？以下信息可能很有帮助：

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [关于 Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

注册 {{site.data.keyword.cloud_notm}} 帐户。有关更多信息，请参阅[注册 {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}。

## 步骤 1 - 确定存储需求
{: #determine-storage-requirements}

您要运行具有较小存储需求的通用工作负载？或者，工作负载 I/O 密集程度需要更高的容量和性能？要了解有关如何确定容量和性能的更多信息，请参阅[块存储器容量和性能](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance)。另请参阅[概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)，以了解哪个 IOPS 概要文件选项能最符合您的存储需求。 

您还要创建虚拟服务器实例？请参阅[虚拟服务器概要文件与存储器概要文件的关系](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage)。

## 步骤 2 - 确定块存储器的大小和价格
{: #size-price-block-storage}

为块存储卷选择 [IOPS 层概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)。（可选）如果预定义的 IOPS 层不满足明确定义的性能需求，请选择[定制 IOPS 概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)。 

选择块存储卷的大小和性能后，请参阅[定价](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing)信息，以帮助您确定卷的价格，并了解如何计费。

## 步骤 3 - 登录到 {{site.data.keyword.cloud_notm}} 帐户
{: block-storage-log-into-ibm-account}

通过 [{{site.data.keyword.cloud_notm}}“目录”](https://{DomainName}/catalog){: external}访问 {{site.data.keyword.block_storage_is_short}} 订购表单。请使用您的 IBM 标识和密码。

## 步骤 4（可选）- 验证对 {{site.data.keyword.vpc_short}} 的访问权

如果要在 Virtual Private Cloud 中创建卷，必须先[创建 VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console)。如果要在 VPC 外部创建独立卷，请跳过此步骤。您可以稍后请求对 {{site.data.keyword.vpc_short}} 的访问权，以访问实例以及连接独立创建的块存储卷。有关 {{site.data.keyword.vpc_short}} 的更多信息，请参阅 [VPC 入门教程](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 步骤 5 - 创建块存储卷

在 [{{site.data.keyword.cloud_notm}} 控制台 (UI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage) 中，或者通过使用 [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) 或 [{{site.data.keyword.vpc_short}} API](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}，开始创建卷。有关使用 IBM Cloud Developer Tools 来安装 IBM Cloud CLI 的更多信息，请参阅 [IBM Cloud Developer Tools 入门](/docs/cli?topic=cloud-cli-getting-started)。

## 后续步骤
{: #next-step-block-storage-getting-started}

创建块存储器后，请探索更多选项：

* [查看有关卷的详细信息](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [管理块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
