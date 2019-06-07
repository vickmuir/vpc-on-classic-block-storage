---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance

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

# Managing block storage volumes using the UI
{: #managing-block-storage}

## Detach a block storage volume from a virtual server instance
{: #detach}

You can detach a block storage volume that is currently attached to a virtual server instance.  Detaching frees the volume for use by another instance.

To detach a volume:

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Locate the volume and then click the elipsis (...) at the end of the table row. A context menu displays.
1. From the menu, click **Detach from instance**.
1. Confirm by clicking **Detach instance** in the popup.

Alternatively, you can click on an individual volume in the list of all block storage volumes and navigate to the  **Volume Details** page for that volume. Under **Attached instances**, click the minus sign next to the virtual server instance to detach the volume from that instance.

## Transfer a block storage volume from one virtual server instance to another
{: #transfer}

To transfer a block storage volume to another virtual server instance:

1. [Detach the volume from its virtual server instance](#detach).
1. Navigate to the virtual server instance to which you want to transfer the volume. In the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Compute > Virtual server instances for VPC**.
1. Select a virtual server from the list.
1. Under Attached Storage volumes, click the plus sign to add a volume. All block storage volumes are displayed.
1. From the list of volumes, select the volume you previously detached.

## Attach a previously-attached block storage volume
{: #reattach}

Block storage volumes are attached by default when you create a new virtual server instance.  When you detach a volume from an instance, it exists as an unattached volume and is displayed in the list of [all block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). You can attach it to another image from the list of block storage volumes.

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, navigate to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Locate the volume and then click the elipsis (...) at the end of the table row. A context menu displays.
1. From the menu, click **Attach to instance**.
1. Select an available virtual server instance.
1. Confirm your selection.

## Rename a volume
{: #rename}

You can change the name of an existing volume to make it more meaningful.

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, go to to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Locate the volume and then click the name of the volume to go to the Volume Details page.
1. Click the pencil icon after the name of the volume and edit the volume name.
1. Confirm your edit.

## Delete a block storage volume
{: #delete}

Deleting a block storage volume completely removes its data. The volume cannot be restored.

You cannot delete an active block storage volume. To delete a volume, first [detach it](#detach) from the virtual server, then follow these steps:

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Locate the volume you want to delete and then click the elipsis at the end of the table row. A context menu displays.
1. From the menu, click **Delete**.
1. Confirm the deletion.

## Automatic deletion of block storage data volumes
{: #auto-delete}

Using the Auto Delete feature, you can specify that a block storage data volume be automatically deleted when you delete a VSI to which it is attached. This feature does not apply to boot volumes and is disabled by default.

To enable Auto Delete for an existing block storage volume attached to a VSI, follow these steps:

1. Locate the virtual server instance to which the volume is attached. In the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, navigate to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Compute > Virtual server instances for VPC**.
1. Under **Attached block storage volumes**, select a volume.
1. On the pop-up menu, click the Auto Delete button to enable.
1. Confirm your selection.

Alternatively, begin by selecting a volume from the list of block storage volumes (**Storage > Block storage volumes for VPC**).

To enable Auto Delete on a new volume when creating a VSI, see [Create and attach a block storage volume when you create a new instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi).

## Assign access to a block storage volume
{: #assign-volume-access}

With Administrator privileges, you can assign volume-level user access to the {{site.data.keyword.block_storage_is_short}} service. The following table shows the information you must provide in the [Identity and Access Management (IAM) UI](/docs/iam?topic=iam-account_setup#assigning-access).

| IAM field | Action |
|--------|-------------|
| Services | Select **Infrastructure Services** |
| Resource Type | Select **Block Storage for VPC** |
| Volume ID | Enter the [volume ID](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) to assign access to a specific volume |
| Select Roles | Assign platform access roles, typically, Operator |

For more information, see the [best practices for assigning access](/docs/iam?topic=iam-account_setup#account_setup). For the complete IAM process, which includes inviting users to your account and assigning Cloud IAM access, see the [IAM getting started tutorial](/docs/iam?topic=iam-getstarted#getstarted).

## Block storage volume status
{: #status}

The following table shows statuses you might see when creating, viewing, or managing your block storage volumes.

| Status | Meaning |
|--------|-------------|
| Available | A volume was retrieved successfully |
| | A volume is available and can be attached to an instance |
| | An attached volume is available for data
| | A boot volume is available |
| Failed    | Volume creation failed |
| | All volumes in a region could not be retrieved |
| | A volume with the specified volume ID could not be found |
| | A volume could not be deleted |
| Pending | A volume is being created |
| | A volume is being attached to an instance |
| Pending deletion | A volume is being deleted |

Do you prefer to manage block storage volumes using the CLI? For information, see [Managing block storage volumes (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli).
{: tip}

## What happens next
{: #next-step-managing-block-storage}

You can [create additional volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

For issues with existing block storage volumes, you might be able to troubleshoot and fix the problems yourself.  For more information, see [Troubleshooting for block storage](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
