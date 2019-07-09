---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

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

# 檢視區塊儲存空間磁區詳細資料
{: #viewing-block-storage}

檢視區塊儲存空間磁區的詳細資料或所有磁區的摘要資訊。

## 檢視所有區塊儲存空間磁區的相關資訊
{: #viewvols}

導覽至區塊儲存空間磁區的清單。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，移至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > VPC 的區塊儲存空間磁區**。

依預設，會顯示您所在地區中所有資源群組的區塊儲存空間磁區。在所有**區塊儲存空間磁區**的清單中，您將看到下列資訊。

| 欄位 | 說明 |
|-------|-------------|
| 狀態 | 磁區的狀態，用作所有列的預設過濾器。如需磁區狀態的相關資訊，請參閱[區塊儲存空間磁區狀態](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status)。|
| 名稱 | 按一下磁區的名稱，以查看個別磁區詳細資料。|
|資源群組| 設定 VPC 時所定義的資源群組。資源群組可管理對資源的存取，但不影響計費或監視。|
| 位置 | 您所在地區中的可用性區域，繼承自 VPC（例如，美國南部 1）。|
| 大小 | 您指定的磁區大小（以 GB 為單位）。|
|最大 IOPS| 磁區上可用的最大 IOPS，由一般用途 IOPS 層級或您指定的自訂 IOPS 值所定義。|
| 連接類型 | 資料（若為連接至實例的次要磁碟區）、開機（以啟動磁區連接時），或空白（若為未連接的磁區）。|
| 加密 | 提供者管理或[客戶管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。|
| 動作 (...) | 按一下省略符號以顯示快速功能表，列出您可以採取的特定動作。例如，可用、未連接的磁區將具有可連接至實例或刪除磁區的功能表選項。|
{: caption="表 1. 所有磁區的詳細資料" caption-side="top"}

依預設，所有區塊儲存空間磁區的清單中會顯示 10 個磁區。按一下向下箭頭來變更此預設值，並將清單增加至 20 或 50 個磁區。請使用右下角的箭頭，來導覽至下一頁然後再返回。

## 檢視區塊儲存空間磁區的詳細資料
{: #view-vol-details}

若要檢視區塊儲存空間磁區的詳細資料，請導覽至所有區塊儲存空間磁區的清單，然後選取一個磁區。若為單一磁區，您會看到下列資訊。

| 欄位 | 說明 |
|-------|-------------|
| 名稱  | 建立磁區時所指定的磁區名稱。按一下鉛筆圖示，以編輯磁區名稱。|
| 資源群組 | 設定 VPC 時所定義的資源群組。資源群組可管理對資源的存取，但不影響計費或監視。|
| 連接類型 | 資料（若為連接至實例的次要磁碟區）、開機（以啟動磁區連接時），或空白（若為未連接的磁區）。|
| ID | 系統產生的磁區 ID。|
| 已建立 | 建立磁區時，系統產生的日期。|
| 位置 | 您所在地區中的可用性區域。|
| 大小 | 您指定的磁區大小。|
| 設定檔 | IOPS 層級或自訂 IOPS 設定檔。|
|最大 IOPS| 預先定義之 IOPS 層級的最大 IOPS 值，或您指定給自訂 IOPS 的值。|
|傳輸量
| 磁碟可提供的效能，以十億位元/秒 (Gbps) 為單位測量。根據您的磁區設定檔，傳輸量會計算為 IOPS * 16K 區塊大小的數量。|
| 加密 | 提供者管理或客戶管理。|
{: caption="表 1. 磁區詳細資料" caption-side="top"}

連接至虛擬伺服器實例的磁區，顯示在**磁區詳細資料**頁面的**連接的實例**下。您也可以[將磁區連接至實例](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)。

對於連接至實例的磁區，您也可以導覽至實例的相關資訊，然後回到所有「區塊儲存空間」磁區的清單。

## 在實例詳細資料中檢視連接的區塊儲存空間磁區詳細資料

您可以從**虛擬伺服器實例詳細資料**頁面，檢視連接的區塊儲存空間磁區的相關資訊：

1. 在 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，移至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 運算 > VPC 的虛擬伺服器實例**，然後選取一個實例。
1. 在**連接的區塊儲存空間磁區**下，按一下磁區的名稱，以移至磁區詳細資料頁面。

您偏好使用 CLI 來檢視區塊儲存空間磁區嗎？如需相關資訊，請參閱[檢視區塊儲存空間磁區 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli)。
{: tip}

## 下一步
{: #next-step-viewing-block-storage}

建立其他磁區或管理現有的區塊儲存空間磁區。

* [在 IBM Cloud 主控台中建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [利用使用者介面管理區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
