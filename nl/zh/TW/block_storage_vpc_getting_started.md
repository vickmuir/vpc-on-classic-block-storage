---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# 入門指導教學
{: #getting-started}

本指導教學協助您開始在 Virtual Private Cloud 上建立 {{site.data.keyword.block_storage_is_short}} 磁區。

## 在開始之前
{: #block-storage-before-you-begin}

若要開始，請先檢閱可協助您實作的內容。您是初次使用 {{site.data.keyword.cloud}} 和 {{site.data.keyword.block_storage_is_short}} 嗎？下列資訊可能會有幫助：

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [關於 Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

註冊 {{site.data.keyword.cloud_notm}} 帳戶。如需相關資訊，請參閱[註冊 {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}。

## 步驟 1 - 判定您的儲存空間需求
{: #determine-storage-requirements}

您是否正在執行具有適度儲存空間需求的一般用途工作負載？或者，您的工作負載是否高度使用 I/O，需要更高的容量和效能？若要進一步瞭解如何判定容量與效能，請參閱 [Block Storage 容量與效能](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance)。另請參閱[設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)，以瞭解哪一個 IOPS 設定檔選項最符合您的儲存空間需求。 

您是否也正在建立虛擬伺服器實例？請參閱[虛擬伺服器設定檔與儲存空間設定檔的關係](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage)。

## 步驟 2 - 調整區塊儲存空間的大小並訂定其價格
{: #size-price-block-storage}

為您的區塊儲存空間磁區選取 [IOPS 層級設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)。如果您有妥善定義但不在預先定義 IOPS 層級內的效能需求，則可以選擇[自訂 IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)。 

在選擇區塊儲存空間磁區的大小和效能之後，請參閱[計價](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing)資訊，以協助您訂定磁區的價格，並瞭解計費方式。

## 步驟 3 - 登入您的 {{site.data.keyword.cloud_notm}} 帳戶
{: block-storage-log-into-ibm-account}

從 [{{site.data.keyword.cloud_notm}} 型錄](https://{DomainName}/catalog){: external}中存取「{{site.data.keyword.block_storage_is_short}} 訂單表格」。請使用您的 IBM ID 和密碼。

## 步驟 4（選用）- 驗證對 {{site.data.keyword.vpc_short}} 的存取

如果您要在 Virtual Private Cloud 內建立磁區，則必須先[建立 VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console)。如果您要在 VPC 外建立獨立式磁區，請跳過此步驟。您可以稍後要求存取 {{site.data.keyword.vpc_short}} 以存取實例，並連接您獨立建立的區塊儲存空間磁區。如需 {{site.data.keyword.vpc_short}} 的相關資訊，請參閱 [VPC 入門指導教學](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 步驟 5 - 建立區塊儲存空間磁區

在 [{{site.data.keyword.cloud_notm}} 主控台（使用者介面）](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)中，或使用 [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) 或 [{{site.data.keyword.vpc_short}} API](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external} 開始建立磁區。如需使用 IBM Cloud Developer 工具來安裝 IBM Cloud CLI 的相關資訊，請參閱[開始使用 IBM Cloud Developer 工具](/docs/cli?topic=cloud-cli-getting-started)。

## 下一步
{: #next-step-block-storage-getting-started}

在建立區塊儲存空間之後，請瀏覽其他選項：

* [檢視磁區的詳細資料](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [管理區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
