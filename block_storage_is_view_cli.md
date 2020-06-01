---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-01-20"

Keywords:

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

# Viewing block storage volumes by using the CLI
{: #viewing-block-storage-cli-gen1}

View details about a block storagee volume or summary information about all volumes from the CLI.
{:shortdesc}

## Before you begin
{: #before-viewing-block-storage-cli-gen1}

1. Make sure that you downloaded, installed, and initialized the following CLI plug-ins:
    * {{site.data.keyword.cloud_notm}} CLI
    * The infrastructure-service plug-in

   For more information, see [IBM Cloud CLI for VPC Reference](/docs/vpc-on-classic?topic=vpc-on-classic-vpc-reference).
   
   When you install the vpc-infrastructure plug-in for the first time, you must set the target generation to gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Make sure that you created an {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## View details about a block storage volume by using the CLI
{: #viewvol-cli-gen1}

Specify this command to show details about a volume.

```bash
ibmcloud is volume VOLUME_ID [--json]
```

Example:

This example uses the volume ID to show volume details.

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

If your volume is attached to a virtual server instance, the name and ID of the volume attachment and instance is also displayed.

## View all block storage volumes by using the CLI
{: #viewall-vol-cli-gen1}

Run this command to list summary information about all volumes:

```bash
ibmcloud is volumes [--json]
```

Example:

The following example shows all volumes for all resource groups in your availability zone.  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

Specifying the resource group ID or name filters the list to volumes that belong to a resource group. When you omit this parameter, it defaults to all resource groups. You can also view all volumes in a particular availability zone.

By default, the first 25 volumes are displayed per page.

## View details about a volume attachment by using the CLI
{: #viewvol-attachment-cli-gen1}

Run this command to view details of a volume attachment to a virtual server instance:

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

Specify an instance ID and a volume attachment ID. Optionally, export the details in JSON format.

## View details about all volume attachments by using the CLI
{: #view-all-volume-attachments-cli-gen1}

Run this command to view all volume attachments for a virtual server instance.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## View volume profiles by using the CLI
{: #viewvol-profiles-cli-gen1}

Run this command to list all volume profiles available in your region.

```bash
ibmcloud is volume-profiles [--json]
```

Example:

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## View a specific volume profile by using the CLI
{: #viewvol-profile-cli-gen1}

Run this command to view a specific volume profile in your region.

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME values are 10iops-tier, 5iops-tier, general-purpose, and custom.

Example:

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

Do you prefer by using the {{site.data.keyword.cloud}} console to view your block storage volumes? For more information, see [Viewing block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-gen1).
{: tip}

## Next steps
{: #next-step-viewing-block-storage-cli-gen1}

Create more volumes or manage your existing block storage volumes.

* [Creating block storage volumes by using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli-gen1)
* [Managing block storage volumes by using the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
