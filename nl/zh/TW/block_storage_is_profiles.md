---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}


# 設定檔
{: #block-storage-profiles}

當您使用 {{site.data.keyword.cloud_notm}} 主控台、 CLI 或 API 來佈建 {{site.data.keyword.block_storage_is_short}} 次要磁區時，您會指定最符合您儲存空間需求的 IOPS 設定檔。設定檔可以作為三個預先定義的 IOPS 層級或自訂 IOPS 使用。IOPS 層級對高達 2 TB 容量的磁區提供保證的 IOPS/GB 效能。您也可以指定自訂 IOPS 設定檔，並在一定範圍內定義磁區容量及 IOPS。

## 分層 IOPS 設定檔
{: #tiers}

區塊儲存空間提供三個預先定義的 IOPS 層級，您可以選取指定運算工作負載的最佳效能並且避免發生瓶頸。您可以使用保證的 IOPS 在可用性區域中佈建磁區，如下表所述：

|IOPS 層級| 工作負載 | 磁區大小 |最大 IOPS|
|-----------|----------|-------------|----------|
| 3 IOPS/GB | 一般用途工作負載 - 為 Web 應用程式管理小型資料庫或儲存 Hypervisor 虛擬機器磁碟映像檔的工作負載 | 10 GB 至 1 TB | 高達 3,000 IOPS |
| | | 超過 1 TB 至 2 TB | 3 IOPS/GB 高達 6,000 IOPS |
| 5 IOPS/GB | 高 I/O 強度工作負載 - 以高百分比的作用中資料為特徵的工作負載，例如交易及其他效能相關的資料庫 | 10 GB 至 600 GB | 高達 3,000 IOPS |
| | | 超過 600 GB 至 2 TB | 5 IOPS/GB 高達 10,000 IOPS|
|10 IOPS/GB | 高要求儲存空間工作負載 - NoSQL 資料庫所建立的資料密集工作負載、用於視訊、機器學習及分析的資料處理 | 10 GB 至 300 GB | 高達 3,000 IOPS |
| | | 超過 300 GB 至 2 TB | 10 IOPS/GB 高達 20,000 IOPS |
{: caption="表 1. IOPS 層級及效能" caption-side="top"}

所有區塊儲存空間 IOPS 層級的最大傳輸量是 750 MB/秒，以 16K 區塊大小為基礎

## 自訂 IOPS 設定檔
{: #custom}

當您有定義明確且不在預先定義 IOPS 層級內的效能需求時，自訂 IOPS 是一個不錯的選項。您可以針對磁區在其磁區大小的範圍內指定磁區的 IOPS 總計，以自訂 IOPS。您可以使用 100 IOPS 至 20,000 IOPS 的範圍佈建磁區。

下表根據磁區大小顯示可用的 IOPS 範圍。

| 磁區大小 (GB) |IOPS 範圍|
|-------------|--------------|
| 10 -39   | 100 - 1,000 |
| 40 - 79 | 100 -2,000 |
| 80 - 99 | 100 - 4,000 |
| 100 - 499 | 100 - 6,000 |
| 500 - 999 | 100 - 10,000 |
| 1,000 - 1,999 | 100 - 20,000 |
{: caption="表 2. 根據磁區大小的可用 IOPS" caption-side="top"}

## 虛擬伺服器設定檔如何與儲存空間設定檔相關
{: #vsi-profiles-relate-to-storage}

虛擬伺服器設定檔是 vCPU 及 RAM 的組合，可以快速地實例化以啟動虛擬伺服器實例。根據您的工作負載需求，您可以選取[三個設定檔系列](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)。這些需求的範圍可以從一般工作負載到 CPU 密集或記憶體密集的工作負載。  

同樣地，儲存空間設定檔（IOPS 層級或自訂）可提供次要磁區的容量及效能範圍。依預設，當您建立虛擬伺服器實例時，會建立 100 GB 主要開機磁區。您也可以建立並連接次要磁區。  
當您在建立實例期間建立次要資料磁區時，請選取儲存空間設定檔，該設定檔與您運算工作負載的儲存空間需求最為相符。一般而言，隨著您運算需求的增加，會需要更高的 IOPS 效能。下表顯示此關係。

| IOPS 層級儲存空間設定檔 | 虛擬伺服器設定檔 |
|-----------------|------------------------|
| 3 IOPS/GB       | [平衡](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced)，用於一般工作負載|
| 5 IOPS/GB       | [運算](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute)，用於密集 CPU 需求|
|10 IOPS/GB | [記憶體](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory)，用於記憶體密集工作負載|

## 檢視 IOPS 設定檔
{: #view-iops-profiles}

您可以使用 {{site.data.keyword.cloud_notm}} 主控台、CLI 或 API 檢視可用的 IOPS 設定檔。

### 使用 IBM Cloud 主控台
{: using-console-iops-profile}

 當您[從 {{site.data.keyword.cloud_notm}} 主控台建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)時，請從下拉功能表選取**層級**。

 另外，選取**自訂**，然後在該磁區大小的範圍內，選取 IOPS 值。按一下儲存空間大小鏈結，以查看大小及 IOPS 範圍的表格。

 ### 使用 CLI
 {: using-cli-iops-profiles}

 若要使用 CLI 檢視可用設定檔的清單，請執行下列指令：
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### 使用 API
{: using-api-iops-profiles}

下列 cURL API 要求會擷取所有磁區設定檔。

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## 相關資訊

如需 {{site.data.keyword.vsi_is_short}} 的「平衡」、「運算」及「記憶體」設定檔的相關資訊，請參閱[設定檔](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)。
