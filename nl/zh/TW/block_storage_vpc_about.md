---

copyright:
  years: 2019
lastupdated: "2019-07-22"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS, HPCS, Key Protect

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 關於 {{site.data.keyword.block_storage_is_short}}
{: #block-storage-about}
[comment]: # (鏈結的說明主題)

{{site.data.keyword.block_storage_is_full}}(VPC) 針對您可以在 {{site.data.keyword.vpc_full}} (VPC) 內佈建的虛擬伺服器實例（實例），提供 Hypervisor 裝載的高效能資料儲存空間。VPC 基礎架構提供跨多個地區和區域的快速調整，以及額外的效能和安全。如需 {{site.data.keyword.vpc_short}} 的相關資訊，請參閱[關於 Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)。
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} 提供主要啟動磁區和次要資料磁區。在實例佈建期間會自動建立並連接啟動磁區。也可以在實例佈建期間建立並連接資料磁區，或將這些磁區作為您稍後可以連接至實例的獨立式磁區。若要保護資料，您可以使用自己的加密金鑰，或選擇 IBM 管理的加密。[IOPS 層級設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)可讓您指定預先定義的磁區效能層次。或者，您可以選擇[自訂 IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，並定義您自己的磁區容量和 IOPS 層次。

## Block Storage for VPC 磁區
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} 提供可連接至實例作為啟動磁區或作為資料磁區的區塊層次資料儲存空間磁區。您最多可以為每個地區配置 750 個區塊儲存空間磁區。您可以將數個區塊儲存空間資料磁區連接至單一實例，以提供額外容量。您可以連接至實例的磁區數目，取決於實例所包含的 vCPU 數目。如需相關資訊，請參閱[磁區連接限制](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)。

### 啟動磁區
{: #block-storage-vpc-boot-volumes}

建立實例時，會自動建立 100 GB 啟動磁區並連接至實例。啟動磁區的最大 IOPS 為 3,000 IOPS。您可以使用[自己的虛擬金鑰](#about-customer-managed-encrytion)，或使用預設[提供者管理](#about-provider-managed-encryption)的加密來加密啟動磁區。無法手動分離及刪除啟動磁區，但在刪除實例時會將其刪除。

### 次要資料磁區
{: #secondary-data-volumes}

區塊儲存空間資料磁區是總容量範圍為 10 GB 到 2000 GB 的次要磁區。資料磁區的最大 IOPS 會根據磁區大小和您選取的 IOPS 層級設定檔而不同。例如，一般用途磁區（最高為 1 TB）的最大 IOPS 為 3,000 IOPS。如需相關資訊，請參閱[分層 IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)。

您可以建立資料磁區作為獨立式磁區，或在佈建實例時建立資料磁區。獨立式磁區會以未連接狀態存在，直到您將磁區連接至實例為止。當您在實例佈建過程中建立資料磁區時，磁區會自動連接至實例。  

區塊儲存空間資料磁區可以連接至您所在地區內的任何可用實例，但須在[特定限制](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)內。刪除實例時，依預設會分離這些磁區。依預設分離可讓您的資料在虛擬伺服器實例生命週期之外持續保存。它只會移除磁區與實例的關聯。您可以在分離資料磁區之後手動刪除它們，或者在建立磁區時，您可以指定在刪除實例時，[自動分離及刪除](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete)它們。

依預設會使用 IBM 管理的加密來加密資料磁區。您可以選擇使用[自己的加密金鑰](#about-customer-managed-encrytion)來加密資料磁區。

## Block Storage 靜態資料加密
{: #encryption}

{{site.data.keyword.cloud_notm}} 極度重視安全，並瞭解能夠加密資料以確保其安全的重要性。在建立實例的過程中建立獨立式磁區或建立磁區時，您可以選擇使用 IBM 提供者管理的加密來保護資料，或使用您自己的加密金鑰。  

### 提供者管理的加密
{: #about-provider-managed-encryption}

依預設，會使用 IBM 提供者管理的加密來加密所有啟動和資料磁區。此服務不會產生額外的成本，也不會對效能造成影響。提供者管理的加密會使用下列業界標準通訊協定：

* AES-256 加密
* 金鑰會在內部使用「金鑰管理交互作業通訊協定 (KMIP)」加以管理
* 儲存空間已經過驗證，符合「美國聯邦資訊處理標準 (FIPS) 出版品 140-2」、「聯邦資訊安全管理法 (FISMA)」、「醫療保險轉移和責任法 (HIPAA)」。儲存空間已經過驗證，符合「支付卡產業 (PCI)」、Basel II、「加州安全違反資訊行為法案 (SB 1386)」及「歐盟資料保護指令 95/46/EC」規範。

### 客戶管理的加密
{: #about-customer-managed-encrytion}

您可以使用自己的加密金鑰來加密區塊儲存空間磁區。若為資料磁區，您可以在建立磁區時指定客戶管理的加密。若為啟動磁區，您可以在實例建立期間編輯啟動磁區內容，並指定客戶管理的加密。如需程序，請參閱[使用客戶管理的加密建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。

使用客戶管理的加密，您的加密金鑰會上傳至金鑰管理服務（{{site.data.keyword.keymanagementservicelong_notm}} 或 {{site.data.keyword.hscrypto}}）。VPC 基礎架構會先找出您事先配置之金鑰管理服務實例中的金鑰，然後將磁區加密。如需必要條件及一次性設定程序，請參閱[使用客戶管理的加密建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。

如需在虛擬伺服器實例佈建期間為磁區建立客戶管理之加密的相關資訊，請參閱[客戶管理的區塊儲存空間加密](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys)。

## 相關資訊

如需在 VPC 中建立及管理實例的相關資訊，請參閱[關於 VPC 的虛擬伺服器](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud)。

若要開始建立 VPC 的區塊儲存空間，請參閱[建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage)。

{{site.data.keyword.block_storage_is_short}} 提供 VPC 的專屬特性，且與標準基礎架構儲存空間不相容。如果您對標準基礎架構上的 {{site.data.keyword.blockstoragefull}} 感興趣，請參閱[{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About)。
{:note}
