---

copyright:
  years: 2019
lastupdated: "2019-06-09"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# About Block Storage for VPC
{: #block-storage-about}
[comment]: # (linked help topic)

{{site.data.keyword.block_storage_is_short}} provides hypervisor-mounted, high-performance data storage for your virtual server instances (VSIs) that you can provision within an {{site.data.keyword.vpc_full}} (VPC). The VPC infrastructure provides rapid scaling across multiple regions and zones, and extra performance and security. For more information about {{site.data.keyword.vpc_short}}, see [About Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about).
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} provides primary boot volumes and secondary data volumes. Boot volumes are automatically created and attached during VSI provisioning. Data volumes can be created and attached during VSI provisoning as well, or as standalone volumes that you can later attach to an instance. To protect your data, you can use your own encryption key or choose IBM-managed encryption. [IOPS tier profiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) let you specify a pre-defined level of performance for your volumes. Or, you can choose a [custom IOPS profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) and define your own volume capacity and IOPS level.

{{site.data.keyword.block_storage_is_short}} provides features unique to the VPC and is not compatible with the classic infrastructure storage. If you're interested in {{site.data.keyword.blockstoragefull}} on the classic infrastructure, see [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).
{:note}

## Block storage for VPC volumes
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} offers block-level data storage volumes that can be attached to a VSI as either a boot volume or as a data volume. You can configure up to 750 block storage volumes per region. You can attach several block storage data volumes to a single instance for extra capacity. The number of volumes you can attach to the VSI depends on how many vCPUs that VSI contains. For more information, see [Volume attachment limits](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits).

### Boot volumes
{: #block-storage-vpc-boot-volumes}

When you create a VSI, a 100 GB boot volume is automatically created and attached to the VSI. The boot volume has a maximum IOPS of 3,000 IOPS. You can encrypt the boot volume by using [your own encyption keys](#about-customer-managed-encrytion) or use the default [provider-managed encryption](#about-provider-managed-encryption). A boot volume can't be manually detached and deleted but it is deleted when you delete the instance.

### Secondary data volumes
{: #secondary-data-volumes}

Block storage data volumes are secondary volumes with total capacity range of 10 GB to 2000 GB. Maximum IOPS for data volumes vary based on volume size and the IOPS tier profile that you selected. For example, the max IOPS for a general purpose volume up to 1 TB is 3,000 IOPS. For more information, see [Tiered IOPS profiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers).

You create data volumes as standalone volumes or when you provision a VSI. Standalone volumes exist in an unattached state until you attach the volume to an instance. When you create a data volume as part of VSI provisioning, the volume is automatically attached to the instance.  

Block storage data volumes can be attached to any available instance within your region, within [certain limits](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits). These volumes are detached by default when the instance is deleted. Detaching by default allows your data to persist beyond the VSI life cycle. It only removes the volume's association with the instance. You can delete data volumes manually after they are detached or, when creating a volume, you can specify that they be [automatically detached and deleted](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete) when the instance is deleted.

Data volumes are encryped by default with IBM-managed encryption. Optionally, you can encrypt data volumes by using [your own encryption key](#about-customer-managed-encrytion).

## Capacity and performance
{: #capacity-performance}

Choosing the optimal block storage volume size and performance level for your workloads is important. When you provision block storage from the UI or CLI, you can choose the size of your volume and performance level.

### Capacity
{: #block-storage-vpc-capacity}

You can specify 10 GB to 2000 GB (2 TB) of capacity per block storage data volume in 1 GB increments. Total volume capacity is determined when you select a [Tiered IOPS profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) or specify a [custom IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) range. Boot volumes are 100 GB.

### IOPS profiles
{: iops-profiles}

When you provision {{site.data.keyword.block_storage_is_short}} volumes, you specify an [IOPS profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) that best meets your storage requirements. Profiles are available as three predefined IOPS tiers or as custom IOPS. [IOPS tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) provide guaranteed IOPS/GB performance for volumes up to 2 TB capacity. You can also specify a [custom IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) profile and define volume capacity and IOPS within a range. Use either the {{site.data.keyword.cloud_notm}} console, CLI, or API to specify a profile.

## How block size affects performance
{: #how-block-size-affects-performance}

IOPS is based on a 16 KB block size with a 50/50 read/write 50% random workload. A 16 KB block is the equivalent of one write to the volume. Baseline throughput is determined by the amount of IOPS multiplied by the 16 KB block size. The higher the IOPS you specify, the higher the throughput. Maximum throughput for a block storage volume is 750 MB/s.

The block size that you choose for your application directly impacts storage performance. If the block size is smaller than 16 KB, the IOPS limit is reached before the throughput limit. Conversely, if the block size is larger than 16 KB, the throughput limit is reached before the IOPS limit. The following table provides some examples of how block size and IOPS affect the throughput.

| Block Size (KB) | IOPS | Throughput (MB/s) |
|-----------------|------|-------------------|
| 4 (typical for Linux) | 1,000 | 4 |
| 8 (typical for Oracle) | 1,000  | 8 |
| 16 | 1,000 | 16 |
| 32 (typical for SQL Server) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="Table 1 shows examples of how block size and IOPS affect the throughput.<br/>Average IO size x IOPS = Throughput in MB/s." caption-side="top"}

## Encryption for data-at-rest
{: #encryption}

{{site.data.keyword.cloud_notm}} takes the need for security seriously and understands the importance of being able to encrypt data to keep it safe. When you create a standalone volume or create a volume as part of VSI creation, you can choose to secure your data with IBM provider-managed encryption or use your own encryption keys.  

### Provider-managed encryption
{: #about-provider-managed-encryption}

By default, all boot and data volumes are encrypted with IBM provider-managed encryption. There is no additional cost for this service or impact on performance. Provider-managed encryption uses the following industry standard protocols:

* AES-256 encryption
* Keys are managed in-house with Key Management Interoperability Protocol (KMIP)
* Storage is validated for Federal Information Processing Standard (FIPS) Publication 140-2, Federal Information Security Management Act (FISMA), Health Insurance Portability and Accountability Act (HIPAA). Storage is also validated for Payment Card Industry (PCI), Basel II, California Security Breach Information Act (SB 1386), and EU Data Protection Directive 95/46/EC compliance.

### Customer-managed encryption
{: #about-customer-managed-encrytion}

You can encrypt block storage volumes with your own encryption keys. For data volumes, you specify customer-managed encryption when creating the volume. For boot volumes, you can edit the boot volume properties during VSI creation and specify customer-managed encryption. For procedures, see [Creating block storage volumes with customer managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

With customer-managed encryption, your encryption key is uploaded to the IBM Key Protect service. The VPC infrastructure locates the key in the Key Protect instance that you configured in advance, and then encrypts the volume. For prerequisites and a one-time set up procedure, see [Creating block storage volumes with customer managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

For more information about creating customer-managed encryption for volumes during virtual server instance provisioning, see [Customer managed encryption for block storage](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys).

## Next steps

For more information about creating and managing VSIs in the VPC, see [About virtual servers for VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

To get started with creating block storage for VPC, see [Creating block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
