---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, block storage volume, volume, volume attachment, virtual server instance, instance

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

# 利用使用者介面連接區塊儲存空間磁區
{: #attaching-block-storage}

從使用者介面建立虛擬伺服器實例的區塊儲存空間磁區時，依預設磁區會連接至該實例。當您分離磁區時，它會以未連接的磁區形式存在，稍後您可以重新連接該磁區。這些可用的磁區會顯示在[所有區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)的清單中。您可以從所有區塊儲存空間磁區的清單中，或在檢視特定實例的詳細資料時，將磁區連接至另一個實例。
{:shortdesc}

## 磁區連接限制
{: #vol-attach-limits}

雖然一次只能將一個區塊儲存空間磁區連接至虛擬伺服器實例，但您可以將數個不同的區塊儲存空間磁區連接至單一實例，限制如下：

* 具有 4 個以下虛擬 CPU 的實例最多可以連接 4 個區塊儲存空間次要磁區，外加啟動磁區。
* 具有 4 個以上虛擬 CPU 的實例最多可以連接 12 個區塊儲存空間次要磁區，外加啟動磁區。

## 將區塊儲存空間磁區連接至虛擬伺服器實例
{: #attach}

從所有區塊儲存空間磁區的清單中，遵循下列步驟。

1. 在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 儲存空間 > VPC 的區塊儲存空間磁區**。
1. 在磁區清單中，按一下列尾端的省略符號，以取得可用、未連接的磁區。即會顯示特定動作快速功能表。
1. 選取**連接至實例**。
1. 從可用資源清單中選取一個運算資源（虛擬伺服器實例），然後按一下**連接**。
1. 訊息會顯示在磁區詳細資料頁面上，指出磁區正連接至映像檔。完成時，映像檔名稱會出現在**連接的實例**下。

您也可以從虛擬伺服器實例詳細資料頁面中連接區塊儲存空間磁區。

1. 在 Virtual Private Cloud 的 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/vpc){: external}中，導覽至**功能表圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > 運算 > VPC 的虛擬伺服器實例**。
1. 從所有虛擬伺服器實例清單中選取實例。如果有任何連接的區塊儲存空間磁區，您會看到它們列示在**連接的區塊儲存空間磁區**下。
1. 選取**連接磁區**。
1. 從可用資源清單中選取一個磁區，然後按一下**連接**。訊息會顯示在實例詳細資料頁面上，指出正在連接磁區。完成時，會更新**連接的區塊儲存空間磁區**清單，以包含新磁區。

您也可以使用 CLI 手動連接區塊儲存空間磁區。如需相關資訊，請參閱[連接區塊儲存空間磁區 (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。
{: tip}

## 下一步
{: #next-step-attaching-block-storage}

建立其他磁區及管理現有磁區。請參閱下列資訊。

* [在 IBM Cloud 主控台中建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [利用使用者介面管理區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
