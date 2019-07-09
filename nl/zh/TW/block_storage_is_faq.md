---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# Block Storage for VPC 常見問題
{: #block-storage-vpc-faq}

## 如何為我的實例配置儲存空間？
{: faq}

建立虛擬伺服器實例時，您可以建立將連接至該實例的[區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)。您也可以[建立獨立式磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol)，稍後將它們連接至您的實例。

## 有多少個實例可以共用所佈建的區塊儲存空間磁區？
{: faq}

區塊儲存空間磁區一次只能連接至一個實例。實例無法共用相同的磁區。

## 可以將多少個區塊儲存空間次要（資料）磁區連接至實例？
{: faq}

具有 4 個以下 vCPU 的實例最多可以連接 4 個區塊儲存空間次要磁區。

具有 4 個以上 vCPU 的實例最多可以連接 12 個區塊儲存空間次要磁區。

## 佈建 IOP 時，是由實例還是磁區強制執行所配置的 IOPS？
{: faq}

IOPS 是在磁區層次上執行。

## 如何測量 IOPS？
{: faq}

IOPS 根據具有隨機 50% 讀取和 50% 寫入之 16 KB 區塊的負載設定檔進行測量。與此設定檔不同的工作負載可能會經歷效能降低。

## 何謂 IOPS 設定檔？
{: faq}

IOPS 設定檔會針對各種容量的磁區定義 IOPS/GB 效能。有三個您可以選取的預先定義 [IOPS 層級](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，這些層級提供保證的 IOPS 效能以符合您的工作負載需求。您也可以定義[自訂 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，並為您選擇的磁區大小指定 IOPS 範圍。當您有妥善定義但不在預先定義 IOPS 層級內的效能需求時，自訂 IOPS 是一個不錯的選擇。

## 對於我的資料磁區，可以預期的最大 IOPS 是多少？
{: faq}

資料磁區的最大 IOPS 會根據磁區大小和您選取的 IOPS 層級設定檔而不同。例如，一般用途磁區（最高為 1 TB）的最大 IOPS 為 3,000 IOPS。如需相關資訊，請參閱[分層 IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)。如果您選擇[自訂 IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，也請定義給定磁區大小的範圍下限和上限。

## 如果我在測量效能時使用較小的區塊大小，會發生什麼情況？
{: faq}

使用較小的區塊大小時，仍然可以取得最大 IOPS，不過，傳輸量會降低。例如，具有 6000 IOPS 的磁區會有下列各種區塊大小的傳輸量：

* 16 KB * 6000 IOPS == ~93.75 MB/秒
* 8 KB * 6000 IOPS == ~46.88 MB/秒
* 4 KB * 6000 IOPS == ~23.44 MB/秒

## 會向我收取使用費嗎？是否有配額限制？
{: faq}

如需如何計費的相關資訊，請參閱 [Block Storagefor VPC 的定價](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing)。適用特定限制。
如需 {{site.data.keyword.cloud}} Virtual Private Cloud 的配額和限制，以及其中可用資源的相關資訊，請參閱[配額](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas)。

## 建立磁區之後，稍後是否可以增加其容量？
{: faq}

否，您無法增加磁區的容量。建議您在佈建區塊儲存空間磁區之前，為預計的成長預估足夠的容量。

## 磁區是否需要預先暖機，才能達到預期的傳輸量？
{: faq}

磁區不需要預先暖機。您可以在佈建磁區後立即看到指定的傳輸量。

## 是否可以建立加密磁區？
{: faq}

所有區塊儲存空間磁區都會藉由 IBM 管理的加密（預設值）或使用您自己的加密金鑰透過 Key Protect 服務進行加密。如需相關資訊，請參閱[使用客戶管理的加密建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。

## 如何分辨磁區具有的加密類型？
{: faq}

從使用者介面中，當您檢視所有區塊儲存空間磁區的清單時，「加密」直欄會指出提供者管理或客戶管理的加密。

若要從 CLI 顯示磁區的內容，請輸入：

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## 我的資料有多安全？
{: faq}

所有區塊儲存空間磁區都會藉由 IBM 管理的加密或使用您自己的加密金鑰進行靜態加密。IBM 管理的金鑰會在 Consul 所備份的區塊儲存空間儲存庫中產生並安全地儲存於其中，然後由系統進行維護。客戶管理的金鑰是使用 IBM Key Protect 服務進行安全管理。

## 我該如何處理災難回復的資料備份？
{: faq}

Block Storage for VPC 可跨您所在地區的備援錯誤區域保護您的資料安全。我們也鼓勵您單獨備份您的資料。您也可以考慮使用 [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started)，這提供災難回復特性，例如磁區複製、Snapshot 及抄寫。

## 可以佈建多少個磁區？
{: faq}

您最多可以為每個地區佈建 1,000 個區塊儲存空間磁區。

## 我應該使用哪個策略來管理我的磁區？
{: faq}

根據預期的成長來決定您需要的容量。佈建之後無法增加磁區大小。不過，您可以視需要建立新的磁區。另外，如果您有明確定義的效能需求，則可以考慮選擇[自訂 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，來提供每個磁區大小的特定 IOPS 範圍。

## 如何建立虛擬伺服器實例的啟動磁碟，以及它與映像檔的相關方式？
{: faq}

佈建虛擬伺服器實例時，會建立開機磁碟（亦稱為啟動磁區）。實例的開機磁碟是虛擬機器映像檔的複製映像檔。刪除連接的實例時，即會刪除啟動磁區。

## 防火牆或安全群組會影響效能嗎？
{: faq}

最佳作法是建議在略過防火牆的 VLAN 上，執行儲存空間資料流量。透過軟體防火牆執行儲存空間資料流量，會增加延遲，而且會對儲存空間效能造成不利的影響。

## 何時可以刪除區塊儲存空間資料磁區？
{: faq}

只有在未連接至虛擬伺服器實例時，您才能刪除區塊儲存空間資料磁區。先[分離磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)，再刪除該磁區。刪除實例時，會分離並刪除啟動磁區。

## 刪除區塊儲存空間資料磁區時，我的資料會發生什麼情況？
{: faq}

刪除區塊儲存空間資料磁區時，會移除該磁區上資料的所有指標，且資料會變成完全無法存取。如果稍後將實體儲存空間重新佈建至另一個帳戶，則會指派一組新的指標。沒有任何新方法，可供這個新帳戶存取可能已在實體儲存空間的任何資料；這組新的指標全都顯示 0。將新資料寫入磁區時，會改寫任何無法存取的資料。

## 我可以從區塊儲存空間中得到的效能延遲為何？
{: faq}

儲存空間內的目標延遲小於 1 毫秒。區塊儲存空間會連接至共用網路上的運算實例，因此，確切的效能延遲將取決於給定時間範圍內的網路資料流量。

## 是否可以在多區域叢集中設定共用儲存空間？
{: faq}

在 IBM Cloud 中，儲存空間選項會本地化至可用性區域。我們不建議跨多個區域管理共用儲存空間。

如果您必須跨多個區域和地區共用資料，請改用 IBM Cloud 資料標準服務選項，例如 {{site.data.keyword.cos_full}} 或 {{site.data.keyword.cloudantfull}}。

## 我在標準基礎架構上具有磁區。是否可以將它們移植到 VPC？
{: faq}

否。VPC 可讓您存取多區域地區中的新可用性區域。運算、網路及儲存空間資源是為在 VPC 中運作而特別設計的。
