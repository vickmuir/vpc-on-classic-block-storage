---

copyright:
  years: 2019
lastupdated: "2019-06-17"

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

# 使用 CLI 檢視區塊儲存空間磁區
{: #viewing-block-storage-cli}

從 CLI 檢視區塊儲存空間磁區的詳細資料或所有磁區的摘要資訊。

## 在開始之前
{: #before-viewing-block-storage-cli}

請確定您已下載、安裝及起始設定下列 CLI 外掛程式：

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} 地區 API CLI

如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} CLI for VPC 參考資料](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)中的必要條件。

## 使用 CLI 檢視區塊儲存空間磁區的詳細資料
{: #viewvol-cli}

請指定下列指令來顯示磁區的詳細資料。

```bash
ibmcloud is volume VOLUME_ID [--json]
```

範例：

這個範例使用磁區 ID 來顯示磁區詳細資料。

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

如果您的磁區連接至虛擬伺服器實例，則也會顯示磁區連接及實例的名稱和 ID。

## 使用 CLI 檢視所有區塊儲存空間磁區
{: #viewall-vol-cli}

請執行下列指令來列出所有磁區的摘要資訊：

```bash
ibmcloud is volumes [--json]
```

範例：

下列範例顯示可用性區域中所有資源群組的所有磁區。  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

指定資源群組 ID 或名稱，會過濾屬於資源群組之磁區的清單。當您省略此參數時，它會預設為所有資源群組。您也可以檢視特定可用性區域中的所有磁區。

依預設，每頁顯示前 25 個磁區。

## 使用 CLI 檢視磁區連接的詳細資料
{: #viewvol-attachment-cli}

請執行下列指令來檢視虛擬伺服器實例之磁區連接的詳細資料：

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

指定實例 ID 和磁區連接 ID。您可以選擇以 JSON 格式匯出詳細資料。

## 使用 CLI 檢視所有磁區連接的詳細資料

請執行下列指令來檢視虛擬伺服器實例的所有磁區連接。

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## 使用 CLI 檢視磁區設定檔
{: #viewvol-profiles-cli}

請執行下列指令來列出您所在地區中可用的所有磁區設定檔。

```bash
ibmcloud is volume-profiles [--json]
```

範例：

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

## 使用 CLI 檢視特定磁區設定檔
{: #viewvol-profile-cli}

請執行下列指令來檢視您所在地區中的特定磁區設定檔。

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME 值為 10iops-tier、5iops-tier、general-purpose 及 custom。

範例：

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

您偏好使用 {{site.data.keyword.cloud}} 主控台來檢視區塊儲存空間磁區嗎？如需相關資訊，請參閱[檢視區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)。
{: tip}

## 下一步
{: #next-step-viewing-block-storage-cli}

建立其他磁區或管理現有的區塊儲存空間磁區。

* [建立區塊儲存空間磁區 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [管理區塊儲存空間磁區 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
