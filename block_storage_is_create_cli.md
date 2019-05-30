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

# Creating block storage volumes using the CLI
{: #creating-block-storage-cli}

You can create {{site.data.keyword.block_storage_is_full}} volumes by using the command line interface (CLI).
{:shortdesc}

## Before you begin

Ensure you have downloaded, installed, and initialized the following CLI plug-ins:

* {{site.data.keyword.cloud_notm}} CLI
* The infrastructure-service plugin

For more information, see the prerequisites in the [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Create a block storage volume using the CLI
{: #create-vol-cli}

Run the following command.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Example:

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-04-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Capacity, indicated in megabytes, can range from 10 to 2,000 GBs.  IOPS values can be 1,000 to 20,000 IOPS, depending on volume size. If you don't specify an IOPS value, it defaults to the valid configuration per volume profile. For information, see the table of [IOPS ranges based on volume size](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).

The volume ID in the above example is used when attaching block storage to a virtual server instance, viewing block storage volume details, and deleting volumes.

Do you prefer to create block storage volumes from the {{site.data.keyword.cloud}} console? For information, see [Creating block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
{: tip}

## What happens next

[Attach a block storage volume (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
