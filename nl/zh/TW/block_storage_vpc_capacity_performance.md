---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

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

# Block Storage 容量及效能
{: #capacity-performance}

為您的工作負載選擇最佳的區塊儲存空間磁區大小及效能層次非常重要。當您從使用者介面或 CLI 佈建區塊儲存空間時，可以選擇磁區大小及效能層次。

### 容量
{: #block-storage-vpc-capacity}

您可以對每個區塊儲存空間資料磁區指定 10 GB 到 2000 GB (2 TB) 的容量（以 1 GB 的增量）。當您選取 [IOPS 設定檔](#iops-profiles)時，會決定磁區容量總計。啟動磁區是 100 GB。

### IOPS 設定檔
{: #iops-profiles}

當您佈建 {{site.data.keyword.block_storage_is_short}} 磁區時，指定最符合您的儲存空間需求的 [IOPS 設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)。設定檔可以作為三個預先定義的 IOPS 層級或自訂 IOPS 使用。[IOPS 層級](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)對高達 2 TB 容量的磁區提供保證的 IOPS/GB 效能。您還可以指定[自訂 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) 設定檔，並在一定的範圍內定義磁區容量及 IOPS。使用 {{site.data.keyword.cloud_notm}} 主控台、CLI 或 API 來指定設定檔。

## 區塊大小影響效能的方式
{: #how-block-size-affects-performance}

IOPS 是以 16 KB 區塊大小為基礎，加上 50/50 讀取/寫入的 50% 隨機工作負載。16 KB 區塊相當於寫入一次磁區。基準線傳輸量是由 IOPS 數量乘以 16 KB 區塊大小決定。您指定的 IOPS 越高，傳輸量就越高。區塊儲存空間磁區的最大傳輸量是 750 MB/秒。

對應用程式選擇的區塊大小會直接影響儲存空間效能。如果區塊大小小於 16 KB，則在達到傳輸量限制之前會先達到 IOPS 限制。相反地，如果區塊大小小於 16 KB，則在達到 IOPS 限制之前會先達到傳輸量限制。下表提供部分範例，說明區塊大小及 IOPS 影響傳輸量的方式。

|區塊大小 (KB)|IOPS|傳輸量（MB/秒）|
|-----------------|------|-------------------|
|4（一般用於 Linux）|1,000| 4 |
|8（一般用於 Oracle）|1,000| 8 |
| 16 |1,000| 16 |
|32（一般用於 SQL Server）|500| 16 |
| 64 | 250 | 16 |
|128 |128 | 16 |
{: caption="表 1 顯示區塊大小及 IOPS 影響傳輸量的方式。<br/>平均 IO 大小 x IOPS = 傳輸量（以 MB/秒為單位）。" caption-side="top"}
