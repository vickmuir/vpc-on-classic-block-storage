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
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Managing block storage volumes using the UI
{: #managing-block-storage-gen1}

Manage your block storage volumes by using the UI. You can detach a volume from a virtual server instance, transfer a volume from one instance to another, attach a previously-attached volume, rename a volume, set automatic volume deletion, manually delete a volume, or assign access to a volume.
{:shortdesc}

## Detach a block storage volume from a virtual server instance
{: #detach-gen1}

You can detach a block storage volume that is currently attached to a virtual server instance.  Detaching frees the volume for use by another instance.

To detach a volume:

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Storage > Block storage**.
1. Locate the volume and then click the elipsis (...) at the end of the table row. A context menu displays.
1. From the menu, click **Detach from instance**.
1. Confirm by clicking **Detach instance** in the popup.

Alternatively, you can click on an individual volume in the list of all block storage volumes and navigate to the  **Volume Details** page for that volume. Under **Attached instances**, click the minus sign next to the virtual server instance to detach the volume from that instance.

## Transfer a block storage volume from one virtual server instance to another
{: #transfer-gen1}

To transfer a block storage volume to another virtual server instance:

1. [Detach the volume from its virtual server instance](#detach-gen1).
1. Navigate to the virtual server instance to which you want to transfer the volume. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
1. Select a virtual server instance from the list.
1. Under Attached Storage volumes, click the plus sign to add a volume. All block storage volumes are displayed.
1. From the list of volumes, select the volume you previously detached.

## Attach a previously-attached block storage data volume
{: #reattach}

A block storage data volume is attached by default when you create the volume during virtual server instance creation. When you detach a volume from an instance, it exists as an unattached volume and is displayed in the list of [all block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-gen1#viewvols-gen1). You can attach it to another instance from the list of block storage volumes.

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Storage > Block storage**.
1. Locate the volume and then click the elipsis (...) at the end of the table row. A context menu displays.
1. From the menu, click **Attach to instance**.
1. Select an available virtual server instance.
1. Confirm your selection.

## Rename a block storage volume
{: #rename}

You can change the name of an existing volume to make it more meaningful.

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Storage > Block storage**.
1. Locate the volume and then click the name of the volume to go to the Volume Details page.
1. Click the pencil icon after the name of the volume and edit the volume name. Provide a [valid volume name](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-gen1#volume-name-conventions-gen1).
1. Confirm your edit.

## Guidelines for naming volumes
{: #volume-name-conventions-gen1}

Valid volume names can include a combination of lowercase alphanumeric characters (a-z, 0-9) and the hyphen (-), up to 63 characters.  Volume names must be unique and must begin with a lowercase letter.

Volume names must be unique across the entire VPC infrastructure. For example, if you create two volumes from Gen 1 and Gen 2 compute resources that are in the same account, the same region, and have the same name, a  "volume name duplicate" error is triggered.

**Note:** Volumes created prior to 2019-10-15 allowed a combination of lowercase and uppercase alpha-numeric characters (A-Z, a-z, 0-9), hyphen (-), and underscore (_). When you rename such a volume, the newer rules apply.



## Delete a block storage data volume
{: #delete-gen1}

Deleting a block storage volume completely removes its data. The volume cannot be restored.

You cannot delete an active block storage volume. To delete a volume, first [detach it](#detach-gen1) from the virtual server instance, then follow these steps:

1. Navigate to the list of all block storage volumes. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Storage > Block storage volumes**.
1. Locate the volume you want to delete and then click the elipsis at the end of the table row. A context menu displays.
1. From the menu, click **Delete**.
1. Confirm the deletion.

## Automatic deletion of block storage data volumes
{: #auto-delete-gen1}

Using the Auto Delete feature, you can specify that a block storage data volume be automatically deleted when you delete an instance to which it is attached.

**Note**: You don't have to set automatic deletion of boot volumes. Boot volumes are created during instance creation and automatic deletion is enabled by default. When you delete the instance, the boot volume is also deleted.

To enable Auto Delete for an existing block storage data volume attached to an instance, follow these steps:

1. Locate the virtual server instance to which the data volume is attached. In the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc), go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
1. Under **Attached block storage volumes**, select a volume.
1. On the next page, click the Auto Delete button to enable.
1. Confirm your selection.

Alternatively, begin by selecting a data volume from the list of block storage volumes (**Storage > Block storage volumes**).

To enable Auto Delete on a new data volume when creating an instance, see [Create and attach a block storage volume when you create a new instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi-gen1).

## Assign access to a block storage volume
{: #assign-volume-access-gen1}

With Administrator privileges, you can assign volume-level user access to the {{site.data.keyword.block_storage_is_short}} service. The following table shows the information you must provide in the [Identity and Access Management (IAM) UI](/docs/iam?topic=iam-account_setup#assigning-access).

| IAM field | Action |
|--------|-------------|
| Services | Select **Infrastructure Services** |
| Resource Type | Select **Block Storage for VPC** |
| Volume ID | Enter the [volume ID](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-gen1#view-vol-details-gen1) to assign access to a specific volume |
| Select Roles | Assign platform access roles, typically, Operator |
{: caption="Table 1. Information for IAM" caption-side="top"}

For more information, see the [best practices for assigning access](/docs/iam?topic=iam-account_setup#account_setup). For the complete IAM process, which includes inviting users to your account and assigning Cloud IAM access, see the [IAM getting started tutorial](/docs/iam?topic=iam-getstarted#getstarted).

## Block storage volume status
{: #status-gen1}

The following table shows statuses you might see when creating, viewing, or managing your block storage volumes.

| Status | Meaning |
|--------|-------------|
| Available | A volume is available and can be attached to an instance |
| | An attached data volume is available |
| | A boot volume is available |
| Failed  | A volume failed to create |
| Pending | A volume is being created |
| Pending deletion | A volume is being deleted |
{: caption="Table 2. Block storage statuses" caption-side="top"}

Do you prefer to manage block storage volumes using the CLI? For information, see [Managing block storage volumes (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
{: tip}

## Next steps
{: #next-step-managing-block-storage-gen1}

You can [create additional volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

For issues with existing block storage volumes, you might be able to troubleshoot and fix the problems yourself. For more information, see [Troubleshooting for block storage](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot-gen1).
