---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-01"

keywords:

subcollection: vpc-on-classic-block-storage

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Attaching a block storage volume by using the CLI
{: #attaching-block-storage-cli-gen1}

A block storage volume attachment connects a volume to a virtual server instance. Each instance can have [many volume attachments](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-gen1#vol-attach-limits-gen1), but a single volume attachment connects one volume to one instance.
{:shortdesc}

## Before you begin
{: #before-attaching-block-storage-cli-gen1}

1. Make sure that you downloaded, installed, and initialized the following CLI plug-ins:
    * {{site.data.keyword.cloud_notm}} CLI
    * The infrastructure-service plug-in

   For more information, see [IBM Cloud CLI for VPC Reference](/docs/vpc-on-classic?topic=vpc-on-classic-vpc-reference).
   
   After you install the vpc-infrastructure plug-in, set the target to generation 1 by running the command `ibmcloud is target --gen 1`.
   {:important}
   
2. Make sure that you already [created an {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Attach a block storage volume by using the CLI
{: #attach-block-storage-cli-gen1}

To attach a volume to a virtual server instance in the current resource group, run this command.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` is the name that you provide for the volume attachment and INSTANCE_ID is the ID of the VSI.

The `VOLUME_ID `specifies the volume that you are attaching.

Specify `--auto-delete true` if you want the volume to be automatically deleted when the VSI is deleted.

To see a list of available virtual server instances, run the `ibmcloud is instances` command.

Example:

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
0738-916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.0.2.1        -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
0738-b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.0.2.2        -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
0738-ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             198.51.100.1     -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
0738-e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             198.51.100.3     -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## Show details of a volume that is attached to a virtual server instance
{: #show-details-attached-vol-gen1}

After you attach a volume, you can display details by specifying the instance ID and volume attachment ID in the `instance-volume-attachment` command.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## List all volume attachments of a server instance
{: #list-all-vol-attachments-gen1}

Use the `instance-volume-attachments` command and specify the instance ID to see all volume attachments for an instance.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

Do you prefer to use the {{site.data.keyword.cloud}} console? For more information, see [Attaching block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-gen1).
{:tip}

## Create a volume attachment JSON
{: #volume_attachment_json-gen1}

When you provision a virtual server instance by using the CLI and create a block storage volume as part of the process, you must specify a volume attachment JSON. The volume attachment JSON, specified in the command or as a file, defines the volume parameters. When you [create an instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) and specify the `--volume-attach` parameter, you specify the volume JSON. For example, `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

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

## Next steps
{: #next-step-attaching-block-storage-cli-gen1}

Create additional volumes and manage existing ones.  See the following information.

* [Create a block storage volume by using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli-gen1#create-vol-cli-gen1)
* [Managing block storage volumes by using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
