---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-01"

keywords:

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# About {{site.data.keyword.block_storage_is_short}}
{: #block-storage-about}
[comment]: # (linked help topic)

{{site.data.keyword.block_storage_is_full}} (VPC) provides hypervisor-mounted, high-performance data storage for your virtual server instances (instances) that you can provision within an {{site.data.keyword.vpc_full}} (VPC). The VPC infrastructure provides rapid scaling across multiple regions and zones, and extra performance and security. For more information about {{site.data.keyword.vpc_short}}, see [About Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about).
{:shortdesc}

Newer generation available. For more information, see [About Block Storage for VPC](/docs/vpc?topic=vpc-block-storage-about) for generation 2 compute resources.
{:important}

{{site.data.keyword.block_storage_is_short}} provides primary boot volumes and secondary data volumes. Boot volumes are automatically created and attached during instance provisioning. Data volumes can be created and attached during instance provisoning as well, or as standalone volumes that you can later attach to an instance. To protect your data, you can use your own encryption key or choose IBM-managed encryption. [IOPS tier profiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#tiers-gen1) let you specify a pre-defined level of performance for your volumes. Or, you can choose a [custom IOPS profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#custom-gen1) and define your own volume capacity and IOPS level.

## Block storage for VPC volumes
{: #block-storage-vpc-volumes-gen1}

{{site.data.keyword.block_storage_is_short}} offers block-level volumes that can be attached to a instance as either a boot volume or as a data volume. You can configure up to 1000 block storage volumes per account in a region. You can attach several block storage data volumes to a single instance for extra capacity. The number of volumes you can attach to an instance depends on how many vCPUs that instance contains. For more information, see [Volume attachment limits](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-gen1#vol-attach-limits-gen1).

### Boot volumes
{: #block-storage-vpc-boot-volumes-gen1}

When you create an instance, a 100 GB boot volume is created and attached to the instance by default. The boot volume has a maximum IOPS of 3,000 IOPS. You can encrypt the boot volume by using [your own encryption keys](#about-customer-managed-encrytion-gen1) or use the default [provider-managed encryption](#about-provider-managed-encryption-gen1). A boot volume can't be manually detached and deleted. Boot volumes are always deleted when you when you delete the instance.

### Secondary data volumes
{: #secondary-data-volumes-gen1}

Block storage data volumes are secondary volumes with total capacity range of 10 GB to 2000 GB. Maximum IOPS for data volumes vary based on volume size and the IOPS tier profile that you selected. For example, the max IOPS for a 5 IOPS/GB volume up to 2 TBs is 10,000 IOPS. For more information, see [Tiered IOPS profiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#tiers-gen1).

You create data volumes as standalone volumes or when you provision an instance. Standalone volumes exist in an unattached state until you attach the volume to an instance. When you create a data volume as part of instance provisioning, the volume is automatically attached to the instance.  

Block storage data volumes can be attached to any available instance within your region, based on your  customer account and permissions, and within [certain limits](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-gen1#vol-attach-limits-gen1). These volumes are detached by default when the instance is deleted. Detaching by default allows your data to persist beyond the virtual server instance life cycle. It only removes the volume's association with the instance. You can delete data volumes manually after they are detached. Also, when you create data volumes, you can specify that they be [automatically deleted](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-gen1#auto-delete-gen1) when the instance is deleted.

Data volumes are encrypted by default with IBM-managed encryption. Optionally, you can encrypt data volumes by using [your own encryption key](#about-customer-managed-encrytion-gen1).

## Block Storage encryption
{: #encryption-gen1}

{{site.data.keyword.cloud_notm}} takes the need for security seriously and understands the importance of being able to encrypt data to keep it safe. When you create a standalone volume or create a volume as part of instance creation, you can choose to secure your data with IBM provider-managed encryption or use your own encryption keys.  

### Provider-managed encryption
{: #about-provider-managed-encryption-gen1}

By default, all boot and data volumes are encrypted with IBM provider-managed encryption for data-at-rest. There is no additional cost for this service or impact on performance. Provider-managed encryption uses the following industry standard protocols:

* AES-256 encryption
* Keys are managed by {{site.data.keyword.cloud_notm}} operations.
* Storage is validated for Federal Information Processing Standard (FIPS) Publication 140-2, Federal Information Security Management Act (FISMA), Health Insurance Portability and Accountability Act (HIPAA). Storage is also validated for Payment Card Industry (PCI), Basel II, California Security Breach Information Act (SB 1386), and EU Data Protection Directive 95/46/EC compliance.

### Customer-managed encryption
{: #about-customer-managed-encrytion-gen1}

You can encrypt block storage volumes with your own encryption keys. For data volumes, you specify customer-managed encryption when creating the volume. Customer-managed encryption protects you data while in transit and while at rest. For added security, you can securely import of your CRKs by using import tokens.

For boot volumes, you can edit the boot volume properties during instance creation and specify customer-managed encryption. For procedures, see [Creating block storage volumes with customer managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

With customer-managed encryption, your encryption key is uploaded to a key management service ({{site.data.keyword.keymanagementservicelong_notm}} or {{site.data.keyword.hscrypto}}) . The VPC infrastructure locates the key in the key management service instance that you configured in advance and then encrypts the volume. For prerequisites and a one-time set up procedure, see [Creating block storage volumes with customer managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

For more information about creating customer-managed encryption for volumes during virtual server instance provisioning, see [this information](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).

## Next Steps
{: #block-storage-vpc-classic-about-next-steps}

Start creating {{site.data.keyword.block_storage_is_short}} volumes.

* For information using the UI, see [Creating block storage volumes by using the UI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* For information using the CLI, see [Creating block storage volumes by using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli-gen1)

## Related information
{: #block-storage-vpc-classic-related-info}

For more information about creating and managing instances in the VPC, see [About virtual servers for VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

{{site.data.keyword.block_storage_is_short}} provides features unique to the VPC and is not compatible with the classic infrastructure storage. If you're interested in {{site.data.keyword.blockstoragefull}} on the classic infrastructure, see [{{site.data.keyword.blockstoragefull}} - Classic](/docs/BlockStorage?topic=BlockStorage-About).
{:note}
