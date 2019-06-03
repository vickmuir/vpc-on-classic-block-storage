---

copyright:
  years: 2019
lastupdated: "2019-05-31"

keywords: block storage, IBM Cloud, VPC, CLI, block storage volume, volume, volume attachment, VSI, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Attaching a block storage volume using the CLI
{: #attaching-block-storage-cli}

A volume attachment connects a block storage volume to a virtual server instance. Each instance can have [many volume attachments](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits), but a single volume attachment connects one volume to one instance.

## Before you begin

Make sure that you downloaded, installed, and initialized the following CLI plug-ins:

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} Regional API CLI

For more information, see the prerequisites in the [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Attach a block storage volume using the CLI
{: #attach-block-storage-cli}

To attach a volume to a virutal server instance in the current resource group, run this command.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` is the name you provide for the volume attachment and INSTANCE_ID is the ID of the VSI.

The `VOLUME_ID `specifies the volume you are attaching.

Specify `--auto-delete true` if you want the volume to be automatically deleted when the VSI is deleted.

To see a list of available virtual server instances, run the `ibmcloud is instances` command.

Example:

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.xxx.xx.xx    -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.xxx.xx.x     -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             192.xxx.xxx.xx   -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             192.xxx.xxx.xxx  -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## Show details of a volume attached to a virtual server instance
{: #show-details-attached-vol}

After you attach a volume, you can display details by specifying the instance ID and volume attachment ID in the `instance-volume-attachment` command.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## List all volume attachments of a server instance

Use the `instance-volume-attachments` command and specify the instance ID to see all volume attachments for a VSI.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

Do you prefer to use the {{site.data.keyword.cloud}} console? For information about how volumes are attached in the console, see [Attaching block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).
{:tip}

## Create a volume attachment JSON
{: #volume_attachment_json}

When you provision a virtual server instance using the CLI and create a block storage volume as part of the process, you must specify a volume attachment JSON. The volume attachment JSON, specified in the command or as a file, defines the volume parameters. When you [create an instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) and specify the `--volume-attach` parameter, you specify the volume JSON. For example, `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

Here is an example volume attachment JSON file that defines a custom volume:

```
[
    {
        "name": "myvolume-attachment",
        "delete_volume_on_instance_delete": true,
        "volume": {
            "name": "myvolume",
            "capacity": 100,
            "iops": 1000,
            "profile": {
                "name": "custom"
            }
        }
    }
]
```
{: screen}

## What happens next

Perform any OS-specific steps to use the Block Storage on the VSI, for example, partition and mount on Linux or Partition/format on Windows. You can now begin writing data to your block storage volume.

You can also create additional volumes and manage existing ones.  See the following information.

* [Create a block storage volume using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [Managing block storage volumes using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
