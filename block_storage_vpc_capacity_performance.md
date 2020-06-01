---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-29"

keywords:

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

# {{site.data.keyword.block_storage_is_short}} capacity and performance
{: #capacity-performance-gen1}

Choosing the optimal block storage volume size and performance level for your workloads is important. When you provision your block storage, you can specify the capacity of your volume and performance level you require.
{:shortdesc}

## Capacity
{: #block-storage-vpc-capacity-gen1}

{{site.data.keyword.block_storage_is_short}} offers a range of storage capacities to meet your requirements. You can specify 10 - 2000 GB (2 TB) of capacity per block storage data volume in 1 GB increments. This capacity depends on the block storage IOPS profile you're using. Boot volumes are always 100 GB.

## Block storage IOPS profiles
{: #iops-profiles}

When you provision block storage data volumes, you specify a [block storage IOPS profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1) that best meets your storage performance requirements. Three predefined tiered profiles are available, or you can choose a custom profile. [IOPS tiered profiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#tiers-gen1) provide dependable IOPS/GB performance for volumes up to 2 TB capacity. [Custom IOPS profiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#custom-gen1) define custom volume capacity/IOPS combinations,within permitted ranges.

## How block size affects performance
{: #how-block-size-affects-performance-gen1}

IOPS is based on a 16 KB block size with a 50-50 read/write 50% random workload. Each 16 KB of data read/written counts as one read/write operation; a single write of less than 16 KB counts as a single write operation.

<!--Writer note: As well as mentioning Write, explain how the limits constrain Reads. What happens exactly when reads/writes are attempted at higher than the allowed limits? Failures? Is throttling applied so that all data will be written but your app experiences delays-->

Baseline throughput is determined by the amount of IOPS multiplied by the 16 KB block size. The higher the IOPS you specify, the higher the throughput. Maximum throughput for a block storage volume is 750 MB/s.

The block size that you choose for your application directly impacts storage performance. If the block size is smaller than 16 KB, the IOPS limit is reached before the throughput limit. Conversely, if the block size is larger than 16 KB, the throughput limit is reached before the IOPS limit. The following table provides some examples of how block size and IOPS affect the throughput, which is calculated as average I/O block size x IOPS = Throughput in MB/s.

| Block Size (KB) | IOPS | Throughput (MB/s) |
|-----------------|------|-------------------|
| 4 (typical for Linux&reg;) | 1,000 | 4 |
| 8 (typical for Oracle) | 1,000  | 8 |
| 16 | 1,000 | 16 |
| 32 (typical for SQL Server) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="Table 1. Examples of how block size and IOPS affect the throughput" caption-side="top"}

Maximum IOPS can still be obtained when you use smaller block sizes, but throughput is less. The following example shows how throughput decreases for smaller block sizes, when max IOPS is maintained.

* 16 KB * 6000 IOPS == ~93.75 MB/sec
* 8 KB * 6000 IOPS == ~46.88 MB/sec
* 4 KB * 6000 IOPS == ~23.44 MB/sec