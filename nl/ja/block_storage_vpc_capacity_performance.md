---

copyright:
  years: 2019
lastupdated: "2019-06-28"

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

# {{site.data.keyword.block_storage_is_short}}の容量とパフォーマンス
{: #capacity-performance}

ワークロードにとって最適なブロック・ストレージのボリューム・サイズとパフォーマンス・レベルを選択することは重要です。 UI または CLI から{{site.data.keyword.block_storage_is_short}}をプロビジョンする際に、ボリュームの容量とパフォーマンス・レベルを選択できます。{:shortdesc}

## 容量
{: #block-storage-vpc-capacity}

ブロック・ストレージ・データ・ボリュームあたり 10 GB から 2000 GB (2 TB) までの容量を、1 GB ずつ増やして指定できます。 合計ボリューム容量は、[IOPS プロファイル](#iops-profiles)を選択すると決まります。 ブート・ボリュームは 100 GB です。

## IOPS プロファイル
{: #iops-profiles}

{{site.data.keyword.block_storage_is_short}} ボリュームのプロビジョン時に、ストレージ要件を最も満たす [IOPS プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)を指定します。 プロファイルには、3 つの事前定義 IOPS ティア・プロファイルとカスタム IOPS プロファイルがあります。 [IOPS ティア](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)で提供される IOPS/GB のパフォーマンスは、最大 2 TB の容量のボリュームまで保証されます。 [カスタム IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) プロファイルを指定して、特定の範囲内でボリューム容量と IOPS を定義することもできます。 プロファイルを指定するには、{{site.data.keyword.cloud_notm}} コンソール、CLI、または API を使用します。

## ブロック・サイズがパフォーマンスに与える影響
{: #how-block-size-affects-performance}

IOPS は、16 KB のブロック・サイズで読み取り 50% 書き込み 50% がランダムに行われるというワークロードに基づきます。 16 KB ブロックは、ボリュームへの 1 回の書き込みに相当します。 ベースライン・スループットは、IOPS の量に 16 KB のブロック・サイズを乗算して求められます。 指定する IOPS が大きいほど、スループットは高くなります。 ブロック・ストレージ・ボリュームの最大スループットは 750 MB/秒です。

アプリケーション用のブロック・サイズの選択内容は、ストレージのパフォーマンスに直接影響します。 このブロック・サイズが 16 KB より小さい場合、スループット限度に達する前に IOPS 限度に到達します。 逆に、このブロック・サイズが 16 KB より大きい場合、IOPS 限度に達する前にスループット限度に到達します。 以下の表は、ブロック・サイズと IOPS によるスループットへの影響の例を示しています。計算された平均 I/O サイズ x IOPS = スループット (MB/秒)。

| ブロック・サイズ (KB) | IOPS | スループット (MB/秒) |
|-----------------|------|-------------------|
| 4 (Linux の場合の標準) | 1,000 | 4 |
| 8 (Oracle の場合の標準) | 1,000  | 8 |
| 16 | 1,000 | 16 |
| 32 (SQL Server の場合の標準) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="表 1. ブロック・サイズと IOPS によるスループットへの影響の例" caption-side="top"}
