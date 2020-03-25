---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-25"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}

# FAQs
{: #block-storage-vpc-faq}

The following questions often arise about {{site.data.keyword.block_storage_is_short}}. If you have other questions you'd like to see addressed here, provide feedback by using the **Open Issue** or **Edit Topic** links.
{:shortdesc}

## How are volumes created and attached to an instance?
{: faq}

When you create a virtual server instance, you can [create a block storage secondary volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi) that is attached to that instance.  ou can also [create a stand-alone volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol) and later attach it to your instance. You can attach several block storage data volumes to a single instance.

## How many instances can share a provisioned block storage volume?
{: faq}

A block storage volume can be attached to only one instance at a time. Instances cannot share a volume.

## How many block storage secondary data volumes can be attached to an instance?
{: faq}

Instances with fewer than 4 cores can attach up to 4 block storage secondary volumes.

Instances with 4 or more cores can attach up to 12 block storage secondary volumes.

## Are the allocated IOPS enforced by instance or by volume?
{: faq}

IOPS is enforced at the volume level.

## What are IOPS profiles and how do they affect volume performance?
{: faq}

IOPS profiles define IOPS/GB performance for volumes of various capacities. There are three predefined [IOPS tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) that you can select that offer reliable IOPS performance for your workload requirements. You can also define [custom IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) and specify a range of IOPS for a volume size you choose. Custom IOPS is a good option when you have well-defined performance requirements that do not fall within a predefined IOPS tier. If you choose a custom IOPS profile, also define a minimum and maximum range for the volume size.

Maximum IOPS for data volumes varies based on volume size and the type of profile you select. For example, the max IOPS for a general-purpose volume up to 1 TB is 3,000 IOPS.

IOPS is measured based on a load profile of 16 KB blocks with random 50% read and 50% writes. Workloads that differ from this profile might experience reduced performance. If you use a smaller block size, maximum IOPS can be obtained but throughput is less. For information, see. How block size affects performance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance#how-block-size-affects-performance).

## How am I charged for usage?
{: faq}

Block Storage for VPC is calculated hourly. The calculation is based on the total number of hours that the block storage volume exists on the account. It exists on the account until you delete the volume or you reach the end of a billing cycle, whichever comes first. For more information, see [Pricing for Block Storage for VPC](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-vpc#pricing-for-block-storage-for-vpc).

## Are there quota limits?
{: faq}

There are quota limits for your block storage volumes based on the number of vCPUs per instance. For more information about quotas and limits for your {{site.data.keyword.cloud}} Virtual Private Cloud and the resources available within it, see [Quotas](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas).

## After creating a volume with specific capacity, can the capacity later be increased?
{: faq}

No, you cannot increase the capacity of a volume. Estimate sufficient capacity for projected growth before you provision a block storage volume.

Also, consider how many volumes you need and the capacity of these volumes. For more informaton, see [Managing volume count and capacity limits](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managingstoragelimits).

## What rules apply to volume names and can I rename a volume later on?
{: faq}

Valid volume names can include a combination of lowercase alphanumeric characters (a-z, 0-9) and the hyphen (-), up to 63 characters.  Volume names must begin with a lowercase letter and be unique across the entire VPC infrastructure.

You can change the name of an existing volume using the UI. See [this information](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#rename) for details.

## Does the volume need to be pre-warmed to achieve expected throughput?
{: faq}

You do not have to pre-warm a volume. You can see the specified throughput immediately upon provisioning the volume.

## How secure is data in a {{site.data.keyword.block_storage_is_short}} volume?
{: faq}

All block storage volumes are encrypted at rest with IBM-managed encryption or using your own encryption keys. IBM-managed keys are generated and securely stored in a block storage vault that is backed by Consul and then maintained by the system. Customer-managed keys are safely managed that uses the IBM Key Protect service or Hyper Protect Crypto Services. For information, see [Creating block storage volumes with customer-managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

To tell what type of encryption you have, when your view your list of all block storage volumes in the UI, the Encryption column indicates either provider-managed or customer-managed encryption. Optionally, show the properties of a volume by by using this CLI command:

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

For extra security, when you delete a volume, all pointers to the data on that volume are removed and the data becomes inaccessible.

## What should I do about data backups for disaster recovery?
{: faq}

Block Storage for VPC secures your data across redundant fault zones in your region. You are are responsible for independently backing up your data.
You might also consider using [{{site.data.keyword.blockstoragefull}}](/docs/BlockStorage?topic=BlockStorage-getting-started), which provides disaster recovery features such as volume cloning, snapshots, and replication.

## How many volumes can be provisioned per account?
{: faq}

You can provision up to 300 block storage volumes per account in a region. You can request your quota to be increased by opening a [support case](https://cloud.ibm.com/unifiedsupport/cases/form){: external}.

## What strategy can I use to manage {{site.data.keyword.block_storage_is_short}} volumes?
{: faq}

Determine the capacity you need based on anticipated growth. Volume size cannot be expanded after provisioning. However, you can create new volumes as needed. Also, if you have well-defined performance requirements, you might consider choosing [custom IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) that provides a specific range of IOPS per volume size.

## How is the boot disk created for an instance and how does it relate to the virtual machine image?
{: faq}

The boot disk, also called a boot volume, is created when you provision a virtual server instance. The boot disk of an instance is a cloned image of the virtual machine image. The boot volume is deleted when you delete the instance to which it's attached.

## When can I delete a block storage data volume?
{: faq}

You can delete a block storage data volume only when it's not attached to a virtual server instance. [Detach the volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach) before deleting it. Boot volumes are detached and deleted when the instance is deleted.

## What happens to the data when I delete a block storage data volume?
{: faq}

When you delete a block storage data volume, all pointers to the data on that volume are removed and the data becomes completely inaccessible. If you later reprovision the physical storage to another account, a new set of pointers are assigned. There is no way for this new account to access any data that might have been on the physical storage; the new set of pointers shows all 0's. When new data is written to the volume, any inaccessible data is overwritten.

## What performance latency can I expect from {{site.data.keyword.block_storage_is_short}}?
{: faq}

Target latency within the storage is less than 1 millisecond. Block storage is connected to compute instances on a shared network, so the exact performance latency depends on the network traffic within a specific timeframe.

## Can I set up shared storage in a multizone cluster?
{: faq}

In the IBM Cloud, storage options are limited to an availability zone. We do not recommend managing shared storage across multiple zones.

Instead, use an IBM Cloud data classic service option such as {{site.data.keyword.cos_full}} or {{site.data.keyword.cloudantfull}} if you must share your data across multiple zones and regions.

## I have volumes on the Classic infrastructure. Can I port them to the VPC?
{: faq}

No. The VPC provides access to new availability zones in multi-zone regions. Compute, network, and storage resources are specifically designed to function in the VPC.
