---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM CLoud, VPC, virtual private cloud, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 使用 CLI 建立區塊儲存空間磁區
{: #creating-block-storage-cli}

您可以使用指令行介面 (CLI) 來建立 {{site.data.keyword.block_storage_is_short}} 磁區。
{:shortdesc}

## 在開始之前
{: #before-creating-block-storage-cli}

1. 請確保您已下載、安裝及起始設定下列 CLI 外掛程式：
    * {{site.data.keyword.cloud_notm}} CLI
    * 基礎架構服務外掛程式

   如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} CLI for VPC 參考資料](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)。
   
   當您第一次安裝 vpc-infrastructure 外掛程式時，必須將目標世代設為 gen 1：`ibmcloud is target --gen 1`。
   {:important}
   
2. 確定您已[建立 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 使用 CLI 建立區塊儲存空間磁區
{: #create-vol-cli}

執行下列指令。

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

範例：

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

容量（以 MB 表示）的範圍可從 10 到 2,000 GB。IOPS 值可以是 1,000 到 20,000 IOPS，取決於磁區大小。如果未指定 IOPS 值，則它會根據磁區設定檔預設為有效的配置。如需相關資訊，請參閱[基於磁區大小的 IOPS 範圍](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)的表格。

將區塊儲存空間連接至虛擬伺服器實例、檢視區塊儲存空間磁區詳細資料，以及刪除磁區時，會使用上述範例中的磁區 ID。

您偏好從 {{site.data.keyword.cloud}} 主控台建立區塊儲存空間磁區嗎？如需相關資訊，請參閱[建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)。
{: tip}

## 下一步
{: #next-step-creating-block-storage-cli}

[連接區塊儲存空間磁區 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。
