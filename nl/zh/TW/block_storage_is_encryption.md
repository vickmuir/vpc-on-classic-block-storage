---

Copyright:
  years: 2019
lastupdated: "2019-07-23"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance, customer-managed encryption

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 使用客戶管理的加密建立區塊儲存空間磁區
{: #block-storage-encryption}

依預設，會使用 IBM 管理的加密來加密 {{site.data.keyword.block_storage_is_short}} 啟動和資料磁區。您也可以建立客戶管理的加密磁區，方法是使用支援的金鑰管理服務來建立或匯入客戶根金鑰。客戶管理的加密是一種選項，用於實例佈建期間所建立的啟動和資料磁區。您也可以在建立獨立式資料磁區時指定客戶管理的加密。{:shortdesc}

## 區塊儲存空間磁區的金鑰管理服務
{: #key-mgt-services-for-storage}

提供兩個金鑰管理服務 {{site.data.keyword.keymanagementserviceshort}} 和 {{site.data.keyword.hscrypto}}（在特定[地區](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)提供）。{{site.data.keyword.cloud_notm}} 資料中心提供專用的 Hardware Security Module (HSM) 來保護您的金鑰。下表提供每個服務的相關資訊。

| 金鑰管理服務 | HSM 加密憑證 |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 *層次 2* 規範 |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 *層次 4* 規範 |
{: caption="表 1. {{site.data.keyword.block_storage_is_short}} 的金鑰管理服務" caption-side="top"}

## 必要條件
{: #custom-managed-vol-prereqs}

若要使用客戶管理的加密來建立區塊儲存空間磁區，您必須先佈建金鑰管理服務，並建立或匯入客戶根金鑰。
您也必須授權 Cloud Block Storage 與金鑰管理服務之間的存取。當您完成了這些必要條件時，就可以開始建立區塊儲存空間磁區，以使用客戶管理的加密。

下列步驟專用於 {{site.data.keyword.keymanagementserviceshort}}，但一般流程也適用於 {{site.data.keyword.hscrypto}}。如果您是使用 {{site.data.keyword.hscrypto}}，請參閱 [{{site.data.keyword.hscrypto}} 資訊](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)，以取得對應的指示。
{:note}

1. 佈建 [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) 服務。

   佈建新的 {{site.data.keyword.keymanagementserviceshort}} 服務實例，可確保它包含區塊儲存空間磁區之客戶管理加密所需的最新更新項目。2019 年建立的 {{site.data.keyword.keymanagementserviceshort}} 實例包含支援客戶管理加密所需的延伸。
   {: tip}

2. 在 {{site.data.keyword.keymanagementservicelong_notm}} 中[建立](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)或[匯入](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys)客戶根金鑰 (CRK)。
3. 從 IBM {{site.data.keyword.iamshort}} (IAM) 中，[授權](/docs/iam?topic=iam-serviceauth#serviceauth) **Cloud Block Storage**（來源服務）與 **{{site.data.keyword.keymanagementserviceshort}}**（目標服務）之間的存取。

## 利用使用者介面建立客戶管理的加密資料磁區
{: #data-vol-encryption-ui}

在實例佈建期間建立新的區塊儲存空間磁區，或將其建立為獨立式磁區時，您可以指定客戶管理的加密。

若要在建立虛擬伺服器實例時建立加密磁區，請參閱[使用客戶管理的加密來建立虛擬伺服器實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok)。

若要在建立獨立式磁區時指定客戶管理的加密，請遵循下列步驟：

1. 在 {{site.data.keyword.cloud_notm}} 主控台中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > VPC 基礎架構 > 儲存空間 > 區塊儲存空間磁區**。
即會顯示所有區塊儲存空間磁區的清單。
1. 選取**新建磁區**。
1. 在**新建區塊儲存空間磁區**頁面上，更新**加密**區段中的欄位。請參閱下表，以取得相關資訊。當您完成變更時，請按一下**建立磁區**。

| 欄位 | 值 |
| ----- | ----- |
| 加密 |_提供者管理_ 是預設加密模式。若要使用客戶管理的加密，請選取金鑰管理服務（{{site.data.keyword.keymanagementserviceshort}} 或 {{site.data.keyword.hscrypto}}）。金鑰管理服務實例應該包含您要用於客戶管理加密的客戶根金鑰。|
| 加密服務實例 | 如果您的帳戶中已佈建多個金鑰管理服務實例，請選取其中包含要用於客戶管理加密的客戶根金鑰的實例。|
| 金鑰名稱 | 選取 {{site.data.keyword.keymanagementserviceshort}} 實例內您要用於加密磁區的資料加密金鑰。|
| 金鑰 ID | 顯示與所選取資料加密金鑰相關聯的金鑰 ID。|
{: caption="表 1. 客戶管理加密的值" caption-side="top"}

## 使用 CLI 建立客戶管理的加密資料磁區
{: #data-vol-encryption-cli}

若要使用 CLI 搭配客戶管理的加密來建立區塊儲存空間磁區，請指定 `ibmcloud is volume-create` 與 `--encryption-key` 參數搭配：

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

`--encryption-key` 參數採用根金鑰的 CRN。請取得金鑰管理服務實例中根金鑰的 CRN。如需相關資訊，請參閱[有關客戶管理加密的虛擬伺服器實例文件](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)。如需使用 CLI 建立區塊儲存空間磁區的相關資訊，請參閱[使用 CLI 建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)。

下列範例顯示使用客戶管理加密所建立的新磁區。

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

在實例佈建期間，您也可以使用客戶管理的加密來建立磁區。如需相關資訊，請參閱[使用 CLI 搭配客戶管理的加密來佈建實例和磁區](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)。

## 利用使用者介面編輯啟動磁區來使用客戶管理的加密

從使用者介面建立實例時，您可以編輯啟動磁區內容來指定客戶管理的加密。如需相關資訊，請參閱[佈建虛擬伺服器實例與使用客戶管理加密的磁區](docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-ui)。
