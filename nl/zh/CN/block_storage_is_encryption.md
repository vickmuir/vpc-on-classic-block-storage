---

Copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 创建使用客户管理的加密的块存储卷
{: #block-storage-encryption}

缺省情况下，{{site.data.keyword.block_storage_is_short}} 引导卷和数据卷使用 IBM 管理的加密进行加密。您还可以使用支持的密钥管理服务创建或导入客户根密钥，以创建客户管理的加密卷。对于在实例供应期间创建的引导卷和数据卷，可以选择“客户管理的加密”选项。还可以在创建独立数据卷时，指定客户管理的加密。  

## 块存储卷的密钥管理服务
{: #key-mgt-services-for-storage}

有两个密钥管理服务可用：{{site.data.keyword.keymanagementserviceshort}} 和 {{site.data.keyword.hscrypto}}（在特定[区域](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)中可用）。{{site.data.keyword.cloud_notm}} 数据中心提供专用 Hardware Security Module (HSM) 来保护密钥。下表提供了有关每个服务的信息。

|密钥管理服务|HSM 加密证书|
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) |符合 FIPS 140-2 *第 2 级*要求|
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) |符合 FIPS 140-2 *第 4 级*要求|

## 先决条件
{: #custom-managed-vol-prereqs}

要创建使用客户管理的加密的块存储卷，必须先供应密钥管理服务，然后创建或导入客户根密钥。您还必须在 Cloud Block Storage 与密钥管理服务之间授予访问权。完成这些先决条件后，即可以开始创建使用客户管理的加密的块存储卷。

以下步骤特定于 {{site.data.keyword.keymanagementserviceshort}}，但一般流程也适用于 {{site.data.keyword.hscrypto}}。如果使用的是 {{site.data.keyword.hscrypto}}，请参阅 [{{site.data.keyword.hscrypto}} 信息](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)以获取相应的指示信息。
{:note}

1. 供应 [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) 服务。

   通过供应新的 {{site.data.keyword.keymanagementserviceshort}} 服务实例，可确保它包含块存储卷的客户管理的加密所需最新更新。2019 年创建的 {{site.data.keyword.keymanagementserviceshort}} 实例包含支持客户管理的加密所需的扩展。
   {: tip}

2. 在 {{site.data.keyword.keymanagementservicelong_notm}} 中，[创建](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)或[导入](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys)客户根密钥 (CRK)。
3. 通过 IBM {{site.data.keyword.iamshort}} (IAM)，[授予访问权](/docs/iam?topic=iam-serviceauth#serviceauth)，即在 **Cloud Block Storage**（源服务）和 **{{site.data.keyword.keymanagementserviceshort}}**（目标服务）之间进行访问的权限。

## 使用 UI 创建客户管理的加密数据卷
{: #data-vol-encryption-ui}

在实例供应期间创建新的块存储卷或将其创建为独立卷时，可以指定客户管理的加密。

要在创建虚拟服务器实例时创建加密卷，请参阅[创建使用客户管理的加密的虚拟服务器实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok)。

要在创建独立卷时指定客户管理的加密，请执行以下步骤：

1. 在 {{site.data.keyword.cloud_notm}} 控制台中，导航至**菜单图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > VPC 基础架构 > 存储 > 块存储卷**。这将显示所有块存储卷的列表。
1. 选择**新建卷**。在“新建块存储卷”页面上，更新“加密”部分中的字段。
1. 在**新建块存储卷**页面上，更新**加密**部分中的字段。请参阅下表以获取更多信息。更改完成后，单击**创建卷**。

|字段|值|
| ----- | ----- |
|加密|_提供者管理_是缺省加密方式。要使用客户管理的加密，请选择密钥管理服务（{{site.data.keyword.keymanagementserviceshort}} 或 {{site.data.keyword.hscrypto}}）。密钥管理服务实例应该包含要用于客户管理的加密的客户根密钥。|
|加密服务实例|如果帐户中供应了多个密钥管理服务实例，请选择包含要用于客户管理的加密的客户根密钥的实例。|
|密钥名称|选择 {{site.data.keyword.keymanagementserviceshort}} 实例中要用于加密卷的数据加密密钥。|
|密钥标识|显示与所选数据加密密钥关联的密钥标识。|
{: caption="表 1. 用于客户管理的加密的值" caption-side="top"}

## 使用 CLI 创建客户管理的加密数据卷
{: #data-vol-encryption-cli}

要使用 CLI 创建使用客户管理的加密的块存储卷，请指定带 `--encryption-key` 参数的 `ibmcloud is volume-create` 命令：

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

`--encryption-key` 参数采用根密钥的 CRN。获取密钥管理服务实例中根密钥的 CRN。有关信息，请参阅[有关客户管理的加密的虚拟服务器实例文档](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)。有关使用 CLI 创建块存储卷的信息，请参阅[使用 CLI 创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)。

以下示例显示使用客户管理的加密创建的新卷。

```bash
$ ibmcloud is volume-create demo_volume custom us-south-1 --iops 1000 --encryption-key abccorp-kp-vpc-2 5437644a-c4b1-447f-9646-b1a2a4df61382
Creating volume demovolume in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          crn:v1:bluemix:public:kms:us-south:a/8d65fb1cf5e99e86dd7229ddef9e5b7b:b1abf7c5-381d-4f34-836e-5db7193250bc:key:fd57250e-908c-4785-a8a5-1f53176bcd2f
Encryption                              customer_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

您还可以在实例供应期间创建使用客户管理的加密的卷。有关信息，请参阅[使用 CLI 供应使用客户管理的加密的实例和卷](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)。

## 使用 UI 编辑引导卷以使用客户管理的加密

通过 UI 创建实例时，可以通过编辑引导卷属性来指定客户管理的加密。有关信息，请参阅[为虚拟服务器实例供应使用客户管理的加密的卷](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#provision-byok-ui)。
