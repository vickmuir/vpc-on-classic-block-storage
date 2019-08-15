---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# 在 {{site.data.keyword.cloud_notm}} 主控台中建立區塊儲存空間磁區
{: #creating-block-storage}
[comment]: # (鏈結的說明主題)

您可以在建立虛擬伺服器實例時建立 {{site.data.keyword.block_storage_is_short}} 磁區，或建立獨立式磁區以稍後連接至實例。
{:shortdesc}

開始之前，請確定已[建立 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

## 建立新實例時，建立及連接區塊儲存空間磁區
{: #create-from-vsi}

1. 建立實例。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 運算 > 虛擬伺服器實例 > 新建實例**。
1. [配置您的虛擬伺服器實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers)。在**連接的區塊儲存空間磁區**下，選取**新建區塊儲存空間磁區**。
1. 輸入下表中說明的資訊。完成時，按一下**建立磁區**。

| 欄位 | 值 |
|-------|-------|
| 名稱  | 為您的磁區指定有意義的名稱（例如，說明運算或工作負載函數的名稱）。您可以輸入字母和數值字元的組合，且稍後可以編輯名稱（如果您想要的話）。|
| 設定檔 | 選取[層級](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，並從 IOP 清單中選取您需要的效能層次。如果您的效能需求未落在預先定義的 IOPS 層級內，請選取[自訂](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)，並選取該磁區大小範圍內的 IOPS 值。按一下**儲存空間大小**鏈結，以查看大小和 IOPS 範圍的表格。|
| 自動刪除 | 啟用此特性，可在連接的虛擬伺服器實例被刪除時，自動刪除此磁區。您稍後可以在虛擬伺服器詳細資料頁面上變更此設定。|
|IOPS| 為「層級」設定檔選取 3、5 或 10 IOPS/GB |
| 大小 | 輸入磁區大小（以 GB 為單位）。磁區大小可在 10 GB 與 2 TB 之間。|
| 加密 | 依預設，在所有磁區上都會啟用「使用 IBM 管理的金鑰進行加密」。您也可以選擇**客戶管理**，並使用您自己的加密金鑰。如需必備條件及步驟，以設定客戶管理的加密，請參閱[使用客戶管理的加密建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。|
{: caption="表 1. 佈建實例時指定的區塊儲存空間磁區值" caption-side="top"}

系統會建立區塊儲存空間磁區，並將其連接至虛擬伺服器實例。在實例詳細資料頁面上，會更新**連接的區塊儲存空間磁區**清單，以包含新磁區。

區塊儲存空間磁區一次只能連接至一部虛擬伺服器。在區塊儲存空間磁區摘要頁面上，您可以在**連接的實例**下選取實例名稱，來檢視虛擬伺服器實例的詳細資料。

## 建立獨立式區塊儲存空間磁區
{: #create-standalone-vol}

您可以建立獨立於虛擬伺服器佈建之外的區塊儲存空間磁區，稍後再將該磁區連接至實例。

1. 在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > 區塊儲存空間磁區**，然後選取**新建磁區**。
1. 在下表中輸入資訊，以定義新的區塊儲存空間磁區。
1. 完成時，按一下**建立磁區**。您會回到「區塊儲存空間磁區」頁面，其中的訊息指出正在建立磁區。建立磁區時，會顯示第二則訊息。
1. 若要查看新磁區的詳細資料，請選取第二則訊息中的**檢視資源**鏈結，以導覽至「磁區詳細資料」頁面。

| 欄位 | 值 |
|-------|-------|
| 名稱  | 為您的磁區指定有意義的名稱。例如，提供一個說明運算或工作負載函數的名稱。您最多可以輸入 40 個英數字元，且可於稍後編輯名稱。|
|資源群組| 指定資源群組。資源群組可基於存取控制及計費目的協助組織您的帳戶資源。如需設定資源群組的相關資訊，請參閱[組織資源群組中資源的最佳作法](/docs/resources?topic=resources-bp_resourcegroups#setuprgs)。|
| 標籤 | 指定標籤來組織資源。標籤是您指派給資源的標籤，可讓您輕鬆過濾資源清單中的資源。如需標籤的相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。|
| 位置 | 您所在地區中的可用性區域，繼承自 VPC（例如，美國南部 1）。|
| 大小 | 輸入磁區大小（以 GB 為單位）。磁區大小可在 10 GB - 2 TB 之間。|
|IOPS| 選取 [IOPS 層級](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)，並選取效能層次為您所需要的磚。|
| 自訂 | 根據您指定的磁區大小，選取在該磁區大小範圍內的 IOPS 值。按一下**儲存空間大小**鏈結，以查看大小和 IOPS 範圍的表格。如需相關資訊，請參閱[自訂 IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)。|
| 加密 | 依預設，在所有磁區上都會啟用「使用 IBM 管理的金鑰進行加密」。若要使用您自己的加密金鑰，請選擇客戶管理的加密選項。如需相關資訊，請參閱[使用客戶管理的加密建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)。|
{: caption="表 2. 用於定義區塊儲存空間磁區的值" caption-side="top"}

您偏好使用 CLI 來建立區塊儲存空間磁區嗎？如需相關資訊，請參閱[使用 CLI 建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)。
{: tip}

## 下一步
{: #next-step-creating-block-storage}

當您重新整理「區塊儲存空間磁區」頁面時，新磁區會出現在磁區清單的頂端。如果已順利建立磁區，它會顯示「可用」狀態。若為獨立式磁區，「連接類型」直欄為空白 (-)。表格列尾端的「動作」功能表 (...) 提供[將區塊儲存空間磁區連接至實例](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)的鏈結。

您可以繼續建立其他區塊儲存空間磁區，或管理現有磁區。

* [檢視區塊儲存空間磁區的詳細資料](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [從虛擬伺服器實例分離磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [刪除區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
