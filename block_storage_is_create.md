---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-29"

keywords:

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Creating block storage volumes by using the UI
{: #creating-block-storage}
[Comment]: # (linked help topic)

In the {{site.data.keyword.cloud_notm}} console, you can create a block storage volume when you create a virtual server instance, or create a stand-alone volume to later attach to an instance.
{:shortdesc}

Newer generation available. For more information, see [Creating block storage volumes by using the UI](/docs/vpc?topic=vpc-creating-block-storage) for generation 2 compute resources.
{:important}

Before you get started, make sure that you [created an {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:note}

## Create and attach a block storage volume when you create a new instance
{: #create-from-vsi-gen1}

1. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
1. Click **New instance**.
1. Follow these instructions to [create your virtual server instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers).
1. To create a block storage volume, under **Attached block storage volumes**, select **New block storage volume**.
1. Enter the information described in the Table 1. When finished, click **Create volume**.

| Field | Value |
|-------|-------|
| Name  | Specify a unique, meaningful name for your volume, for example, a name that describes your compute or workload function. The volume name can be up to 63 lowercase alpha-numeric characters and include the hyphen (-), and must begin with a lowercase letter. You can later edit the name if you want. <br> **Note:** Volume names must be unique the entire VPC infrastructure. For example, if you create two volumes from Gen 1 and Gen 2 compute resources that are in the same account, the same region, and have the same name, a  "volume name duplicate" error is triggered. </br>|
| Profile | Select [Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#tiers-gen1) and select the performance level that you require from the IOPS list. If your performance requirements don't fall within a predefined IOPS tier, select [Custom](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#custom-gen1) and select an IOPS value within the range for that volume size. Click the **storage size** link to see a table of size and IOPS ranges. |
| Auto Delete | Enable this feature to automatically delete this volume when the attached virtual server instance is deleted. You can change this setting later on the virtual server details page. |
| IOPS | Select 3, 5, or 10 IOPS/GB for a Tiered profile |
| Size | Enter a volume size in GBs. Volume sizes can be between 10 GB and 2 TBs. |
| Encryption | Encryption with IBM-managed keys is enabled by default on all volumes. You can also choose **Customer Managed** and use your own encryption key. For prerequistes and steps to set up customer-managed encryption, see [Creating block storage volumes with customer-managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Table 1. Block storage volume values specified when provisioning an instance" caption-side="top"}

A block storage volume is created and attached to the virtual server instance. On the instance details page, the **Attached block storage volumes** list is updated to show the new volume.

A block storage volume can be attached to only one virtual server at a time. On the block storage volume summary page, you can view details about the virtual server instance by selecting the instance name under **Attached instances**.

## Create a stand-alone block storage volume
{: #create-standalone-vol-gen1}

You can create a block storage volume independent of virtual server provisioning and attach the volume to an instance later.

1. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Storage > Block storage volumes**.
1. Select **New volume**.
1. Enter the information in Table 2 to define your new block storage volume.
1. When finished, click **Create volume**. You're returned to the Block storage volumes page, where a message indicates that the volume is being created. A second message displays when the volume is created.
1. To see details of the new volume, select the **View resource** link in the second message to go to the Volume details page.

| Field | Value |
|-------|-------|
| Name  | Specify a unique, meaningful name for your volume. The volume name can be up to 63 lowercase alpha-numeric characters and include the hyphen (-), and must begin with lowercase letter. Volume names must be unique across the entire VPC infrastructure. You can later edit the name if you want. |
| Resource Group | Specify a resource group. Resource groups help organize your account resources for access control and billing purposes. For more information, see [Best practices for organizing resources in a resource group](/docs/resources?topic=resources-bp_resourcegroups#setuprgs). |
| Tags | Specify a tag to organize your resources. A tag is a label that you assign to a resource for easy filtering of resources in your resource list. For more information about tags, see [Working with tags](/docs/resources?topic=resources-tag). |
| Location | The availability zone in your region, inherited from the VPC (for example, US South 1). |
| Size | Enter a volume size in GBs. Volume sizes can be between 10 GB - 2 TBs. |
| IOPS | Select [IOPS Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#tiers-gen1) and select the tile with performance level you require. |
| Custom | Depending on the size of the volume you specified, select an IOPS value within the range for that volume size.  Click the **storage size** link to see a table of size and IOPS ranges. For more information, see [Custom IOPS profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles-gen1#custom-gen1). |
| Encryption | Encryption with IBM-managed keys is enabled by default on all volumes. To use your own encryption keys, choose a customer-managed encryption option. For more information, see [Creating block storage volumes with customer-managed encryption](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).|
{: caption="Table 2. Values for defining a block storage volume" caption-side="top"}

Do you prefer to create block storage volumes by using the CLI? For more information, see [Creating block storage volumes that use the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli-gen1).
{: tip}

## Next steps
{: #next-step-creating-block-storage-gen1}

When you refresh the Block storage volumes page, the new volume appears at the beginning of the list of volumes. If the volume was created successfully, it shows a status of Available. For stand-alone volumes, the Attachment Type column is blank (-). The Action menu (...) at the end of a table row provides a link for [attaching a block storage volume to an instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-gen1).

You can continue creating more block storage volumes or manage existing volumes.

* [View details about a block storage volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-gen1)
* [Detach a volume from a virtual server instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-gen1#detach-gen1)
* [Delete a block storage volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-gen1#delete-gen1)
