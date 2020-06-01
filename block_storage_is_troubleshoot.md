---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-29"

keywords:

subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Troubleshooting {{site.data.keyword.block_storage_is_short}}
{: #troubleshoot-gen1}

When you create or manage block storage volumes, you might encounter issues. Often, you can recover by following a few easy steps. Issues, symptoms, likely causes, and resolutions are described in the following sections.
{:shortdesc}

## Cannot retrieve a volume in a specified region
{: #troubleshoot-topic1-gen1}
{: troubleshoot}

Information about a block storage volume or volumes could not be retrieved for a region.
{: tsSymptoms}

Any of the following causes might apply:

* The volume name and information is missing in either the UI or CLI output.
* You might also be attempting to access a volume in a region other than your region.
* You might be trying to access a generation 2 volume.
{: tsCauses}

Verify that the volume wasn't detached from a virtual server instance and deleted. Search for the instance to which you last attached the volume from the list of all virtual server instances:

1. In [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/vpc){: external}, go to **Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Compute > Virtual server instances**.

1. Select a virtual server instance from the list of all virtual servers.

If the volume is not attached as expected and does not appear in the list of volumes, it was probably deleted.  Because deleting a volume completely removes its data, it cannot be restored.  

If you use the CLI, verify that you entered the correct syntax for viewing volumes. See [View all block storage volumes from the CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-gen1#viewvols-gen1). Verify that you specified the correct resource group or zone.
{: tsResolve}

## Cannot delete a volume by name or ID
{: #troubleshoot-topic2-gen1}
{: troubleshoot}

You can't delete a block storage volume by name or ID.
{: tsSymptoms}

The volume name and ID are not accepted.
{: tsCauses}

Verify that the volume name or identifier is correct and that the volume is not attached to a virtual server instance. Also, verify that the volume is not in a pending state.
{: tsResolve}
