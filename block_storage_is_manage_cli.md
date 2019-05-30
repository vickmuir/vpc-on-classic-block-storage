---

copyright:
  years: 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Managing block storage volumes using the CLI
{: #managing-block-storage-cli}

This information applies to {{site.data.keyword.cloud}} Virtual Private Cloud in the Classic Infrastructure environment.
{: important}

## Before you begin

Make sure that you downloaded, installed, and initialized the following CLI plug-ins:

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} Regional API CLI

For more information, see the prerequisites in the [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Update the name of a volume
{: #update-vol-name}

To change a volume name, specify either the volume name or ID and then indicate the new name.

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

Example:

```bash
$ ibmcloud is volume-update 933c8781-f7f5-4a8f-8a2d-3bfc711788ee --name demo-volume-update
Updating volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount 01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo-volume-update
Capacity                                100
IOPS                                    1000
Auto delete                             false
Encryption                              provider managed
Profile                                 custom
Status                                  available
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Volume Attachment Instance Reference    none
```
{: screen}

## Update a volume attachment using the CLI
{: #update-vol-name-cli}

You can update the volume attachment name and change the default auto delete setting with the `instance-volume-attachment-update` command.

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

Use the `--name` parameter and specify a new name for the volume attachment.

Specify`--auto-delete true` to automatically delete the volume when you delete the VSI to which it's attached.

## Detach a volume using the CLI
{: #detach-vol-attachment-cli}

Use the `instance-volume-attachment-detach` command to detach a volume from a VSI and delete the volume attachment. The block storage volume is not deleted; you can later [attach it to another instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## Delete a block storage volume using the CLI
{: #delete-vol-cli}

Use the `volume-delete` command and specify the volume ID to delete a block storage volume.

**Note:** You cannot delete an active block storage volume. You must first [detach it from the virtual server](#detach-vol-attachment-cli).

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

Example:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

Do you prefer to manage block storage volumes using the {{site.data.keyword.cloud}} console? For more information, see [Managing block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage).
{:tip}

## What happens next

[Create more volumes using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

For issues with existing block storage volumes, you might be able to troubleshoot and fix the problems yourself. For more information, see
[Troubleshooting for block storage](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
