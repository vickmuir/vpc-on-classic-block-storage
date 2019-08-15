---

copyright:
  years: 2019
lastupdated: "2019-07-03"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

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

# 使用 CLI 查看块存储卷
{: #viewing-block-storage-cli}

通过 CLI 查看有关 {{site.data.keyword.block_storage_is_short}} 卷的详细信息或有关所有卷的摘要信息。
{:shortdesc}

## 开始之前
{: #before-viewing-block-storage-cli}

1. 确保已下载、安装并初始化以下 CLI 插件：
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 插件

   有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} CLI for VPC 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)。
   
   首次安装 vpc-infrastructure 插件时，必须将目标生成设置为 gen 1：`ibmcloud is target --gen 1`。
   {:important}
   
2. 请确保您已[创建 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 使用 CLI 查看有关块存储卷的详细信息
{: #viewvol-cli}

指定以下命令来显示有关卷的详细信息。

```bash
ibmcloud is volume VOLUME_ID [--json]
```

示例：

此示例使用卷标识来显示卷详细信息。

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

如果卷连接到虚拟服务器实例，那么还会显示卷连接和实例的名称和标识。

## 使用 CLI 查看所有块存储卷
{: #viewall-vol-cli}

运行以下命令来列出有关所有卷的摘要信息：

```bash
ibmcloud is volumes [--json]
```

示例：

以下示例显示了可用性专区中所有资源组的所有卷。  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

指定资源组标识或名称将过滤列表，以仅显示属于该资源组的卷。省略此参数时，缺省为显示所有资源组。还可以查看特定可用性专区中的所有卷。

缺省情况下，每个页面都会显示前 25 个卷。

## 使用 CLI 查看有关卷连接的详细信息
{: #viewvol-attachment-cli}

运行以下命令来查看虚拟服务器实例的卷连接的详细信息：

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

指定实例标识和卷连接标识。（可选）以 JSON 格式导出详细信息。

## 使用 CLI 查看有关所有卷连接的详细信息

运行以下命令来查看虚拟服务器实例的所有卷连接。

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## 使用 CLI 查看卷概要文件
{: #viewvol-profiles-cli}

运行以下命令来列出区域中可用的所有卷概要文件。

```bash
ibmcloud is volume-profiles [--json]
```

示例：

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## 使用 CLI 查看特定卷概要文件
{: #viewvol-profile-cli}

运行以下命令来查看区域中的特定卷概要文件。

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME 值为 10iops-tier、5iops-tier、general-purpose 和 custom。

示例：

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

您希望使用 {{site.data.keyword.cloud}} 控制台来查看块存储卷？有关信息，请参阅[查看块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)。
{: tip}

## 后续步骤
{: #next-step-viewing-block-storage-cli}

创建更多卷或管理现有块存储卷。

* [使用 CLI 创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [使用 CLI 管理块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
