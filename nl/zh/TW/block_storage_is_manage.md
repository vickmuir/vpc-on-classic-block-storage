---

copyright:
  years: 2019
lastupdated: "2019-07-11"

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

# 利用使用者介面管理區塊儲存空間磁區
{: #managing-block-storage}

從使用者介面管理 {{site.data.keyword.block_storage_is_short}}。從虛擬伺服器實例分離磁區、將磁區從某個實例傳送至另一個實例、連接先前連接的磁區、重新命名磁區、設定自動磁區刪除、手動刪除磁區，或指派磁區存取權。
{:shortdesc}

## 從虛擬伺服器實例分離區塊儲存空間磁區
{: #detach}

您可以分離目前連接至虛擬伺服器實例的區塊儲存空間磁區。分離可以釋出磁區，以供另一個實例使用。

若要分離磁區，請執行下列動作：

1. 導覽至所有區塊儲存空間磁區的清單。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，移至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > 區塊儲存空間**。
1. 找出磁區，然後按一下表格列尾端的省略符號 (...)。即會顯示快速功能表。
1. 從功能表中，按一下**從實例分離**。
1. 按一下蹦現畫面中的**分離實例**以確認。

或者，您也可以按一下所有區塊儲存空間磁區清單中的個別磁區，然後導覽至該磁區的**磁區詳細資料**頁面。在**連接的實例**下，按一下虛擬伺服器實例旁邊的減號，將磁區從該實例分離。

## 將區塊儲存空間磁區從某個虛擬伺服器實例傳送至另一個虛擬伺服器實例
{: #transfer}

若要將區塊儲存空間磁區傳送至另一個虛擬伺服器實例，請執行下列動作：

1. [從虛擬伺服器實例中分離磁區](#detach)。
1. 導覽至您要將磁區傳送至其中的虛擬伺服器實例。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，移至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 運算 > 虛擬伺服器實例**。
1. 從清單中選取虛擬伺服器。
1. 在「連接的儲存空間磁區」下，按一下加號以新增磁區。即會顯示所有區塊儲存空間磁區。
1. 從磁區清單中，選取先前分離的磁區。

## 連接先前連接的區塊儲存空間磁區
{: #reattach}

當您建立新的虛擬伺服器實例時，依預設會連接區塊儲存空間磁區。當您從實例分離磁區時，它會以未連接的磁區形式存在，且會顯示在[所有區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)的清單中。您可以從區塊儲存空間磁區的清單中，將它連接至另一個映像檔。

1. 導覽至所有區塊儲存空間磁區的清單。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > 區塊儲存空間**。
1. 找出磁區，然後按一下表格列尾端的省略符號 (...)。即會顯示快速功能表。
1. 從功能表中，按一下**連接至實例**。
1. 選取可用的虛擬伺服器實例。
1. 確認您選取的項目。

## 重新命名區塊儲存空間磁區
{: #rename}

您可以變更現有磁區的名稱，讓它更有意義。

1. 導覽至所有區塊儲存空間磁區的清單。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，移至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > 區塊儲存空間**。
1. 找出磁區，然後按一下磁區的名稱，以移至「磁區詳細資料」頁面。
1. 按一下磁區名稱之後的鉛筆圖示，然後編輯磁區名稱。
1. 確認您的編輯。

## 刪除區塊儲存空間磁區
{: #delete}

刪除區塊儲存空間磁區會完全移除其資料。因此，無法還原該磁區。

您無法刪除作用中的區塊儲存空間磁區。若要刪除磁區，請先從虛擬伺服器[分離磁區](#detach)，然後遵循下列步驟：

1. 導覽至所有區塊儲存空間磁區的清單。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，移至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > 區塊儲存空間**。
1. 找出您要刪除的磁區，然後按一下表格列尾端的省略符號。即會顯示快速功能表。
1. 從功能表中，按一下**刪除**。
1. 確認刪除。

## 自動刪除區塊儲存空間資料磁區
{: #auto-delete}

使用「自動刪除」特性，您可以指定在刪除所連接的實例時自動刪除區塊儲存空間資料磁區。此特性不適用於啟動磁區，依預設會停用此特性。

若要針對連接至實例的現有區塊儲存空間磁區啟用「自動刪除」，請遵循下列步驟：

1. 找出磁區所連接的虛擬伺服器實例。在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 運算 > 虛擬伺服器實例**。
1. 在**連接的區塊儲存空間磁區**下，選取一個磁區。
1. 在蹦現功能表上，按一下「自動刪除」按鈕以啟用。
1. 確認您選取的項目。

或者，從區塊儲存空間磁區的清單（**儲存空間 > 區塊儲存空間**）中選取一個磁區以開始。

若要在建立實例時對新磁區啟用「自動刪除」，請參閱[建立新實例時建立並連接區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)。

## 指派區塊儲存空間磁區的存取權
{: #assign-volume-access}

您可以使用「管理者」專用權，將磁區層次使用者存取權指派給 {{site.data.keyword.block_storage_is_short}} 服務。下表顯示您必須在 [Identity and Access Management (IAM) 使用者介面](/docs/iam?topic=iam-account_setup#assigning-access)中提供的資訊。

| IAM 欄位 |動作 |
|--------|-------------|
| 服務 | 選取**基礎架構服務** |
| 資源類型 | 選取 **Block Storage for VPC** |
| 磁區 ID | 輸入[磁區 ID](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details)，以指派特定磁區的存取權 |
| 選取角色 | 指派平台存取角色（通常是「操作員」）|
{: caption="表 1. IAM 的資訊" caption-side="top"}

如需相關資訊，請參閱[指派存取權的最佳作法](/docs/iam?topic=iam-account_setup#account_setup)。如需完整的 IAM 處理程序（包括邀請使用者加入您的帳戶，及指派 Cloud IAM 存取權），請參閱 [IAM 入門指導教學](/docs/iam?topic=iam-getstarted#getstarted)。

## 區塊儲存空間磁區狀態
{: #status}

下表顯示您在建立、檢視或管理區塊儲存空間磁區時可能會看到的狀態。

| 狀態 |      意義
    |
|--------|-------------|
| 可用 | 已順利擷取磁區 |
| | 磁區可供使用，且可以連接至實例 |
| | 連接磁區可供資料使用
| | 啟動磁區可供使用 |
| 失敗    | 磁區建立失敗 |
| | 無法擷取地區中的所有磁區 |
| | 找不到具有指定磁區 ID 的磁區 |
| | 無法刪除磁區 |
| 擱置中 | 正在建立磁區 |
| | 磁區正在連接至實例 |
| 刪除擱置中 | 正在刪除磁區 |
{: caption="表 2. 區塊儲存空間狀態" caption-side="top"}

您偏好使用 CLI 來管理區塊儲存空間磁區嗎？如需相關資訊，請參閱[管理區塊儲存空間磁區 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)。
{: tip}

## 下一步
{: #next-step-managing-block-storage}

您可以[建立其他磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)。

對於現有區塊儲存空間磁區的問題，您或許能夠自行疑難排解並修正問題。如需相關資訊，請參閱[區塊儲存空間的疑難排解](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)。
