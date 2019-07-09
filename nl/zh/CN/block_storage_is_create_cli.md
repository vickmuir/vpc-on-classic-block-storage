---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 使用 CLI 创建块存储卷
{: #creating-block-storage-cli}

您可以使用命令行界面 (CLI) 来创建 {{site.data.keyword.block_storage_is_full}} 卷。
{:shortdesc}

## 开始之前
{: #before-creating-block-storage-cli}

确保已下载、安装并初始化以下 CLI 插件：

* {{site.data.keyword.cloud_notm}} CLI
* infrastructure-service 插件

有关更多信息，请参阅 [IBM Cloud CLI for VPC 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)中的先决条件。

## 使用 CLI 创建块存储卷
{: #create-vol-cli}

运行以下命令。

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

示例：

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

容量（以兆字节为单位）的范围为 10 GB 到 2,000 GB。IOPS 值可以介于 1,000 到 20,000 IOPS 之间，具体取决于卷大小。如果未指定 IOPS 值，那么会根据卷概要文件缺省为有效配置。有关信息，请参阅[基于卷大小的 IOPS 范围](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)表。

在将块存储器连接到虚拟服务器实例，查看块存储卷详细信息和删除卷时，将使用以上示例中的卷标识。

您希望通过 {{site.data.keyword.cloud}} 控制台来创建块存储卷？有关信息，请参阅[创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)。
{: tip}

## 后续步骤
{: #next-step-creating-block-storage-cli}

[连接块存储卷 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。
