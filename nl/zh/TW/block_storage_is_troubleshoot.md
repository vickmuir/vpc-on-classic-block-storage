---

copyright:
  years: 2019
lastupdated: "2018-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot


subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# 區塊儲存空間的疑難排解
{: #troubleshoot}

當您建立或管理區塊儲存空間時，可能會發生問題。通常，您可以遵循一些簡單的步驟來回復。下列各節說明問題、症狀、可能原因及解決方案。
{:shortdesc}

## 無法擷取指定區域中的磁區
{: #troubleshoot-topic-1}

無法擷取給定區域的一個以上區塊儲存空間磁區的相關資訊。
{: tsSymptoms}

可能適用於下列任何原因：

* UI 或 CLI 輸出中缺少磁區名稱及資訊。
* 您也可能嘗試在您的區域以外的區域中存取磁區。
* 您可能正在嘗試存取第 2 代磁區。
{: tsCauses}

驗證磁區未與虛擬伺服器實例分離，並且已遭刪除。從所有虛擬伺服器實例的清單中搜尋您前次連接磁區的實例：

1. 在 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![功能表圖示](../../icons/icon_hamburger.svg) > 運算 > 虛擬伺服器實例**。

1. 從所有虛擬伺服器的清單中，選取一個虛擬伺服器實例。

如果磁區未如預期連接，且未顯示在磁區清單中，則可能已將其刪除。因為刪除磁區會完全移除其資料，所以無法將其還原。  

如果您使用 CLI，請驗證已輸入正確的語法來檢視磁區。請參閱[從 CLI 檢視所有區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。請驗證您已指定正確的資源群組或區域。
{: tsResolve}

## 無法依名稱或 ID 刪除磁區
{: #troubleshoot-topic-2}

您無法依名稱或 ID 刪除區塊儲存空間磁區。
{: tsSymptoms}

不接受磁區名稱及 ID。
{: tsCauses}

請驗證磁區名稱或 ID 是否正確，且磁區未連接至虛擬伺服器實例。此外，請驗證磁區未處於擱置狀態。
{: tsResolve}
