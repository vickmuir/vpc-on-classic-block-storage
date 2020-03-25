---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-24"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# {{site.data.keyword.block_storage_is_short}} profiles
{: #block-storage-profiles}

When you provision {{site.data.keyword.block_storage_is_short}} secondary volumes by using the {{site.data.keyword.cloud_notm}} console, CLI, or API, you specify an IOPS profile that best meets your storage requirements. Profiles are available as three predefined IOPS tiers or as custom IOPS. IOPS tiers provide reliable IOPS/GB performance for volumes up to 2 TB capacity. You can also specify a custom IOPS profile and define volume capacity and IOPS within a range.
{:shortdesc}

## Tiered IOPs profiles
{: #tiers}

Block storage provides three predefined IOPS tiers you can select to specify optimal performance for your compute workloads and help avoid bottlenecks. Table 1 describes the IOPS performance that you can expect when create volumes in your availability zone.

| IOPS Tier | Workload | Volume size | Max IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | General-purpose workloads - Workloads that host small databases for web applications or store virtual machine disk images for a hypervisor | 10 GB to 1 TB | Up to 3,000 IOPS |
| | | More than 1 TB to 2 TB | 3 IOPS/GB up to 6,000 IOPS |
| 5 IOPS/GB | High I/O intensity workloads - Workloads characterized by a large percentage of active data, such as transactional and other performance-sensitive databases| 10 GB to 600 GB | Up to 3,000 IOPS |
| | | More than 600 GB to 2 TB | 5 IOPS/GB up to 10,000 IOPS |
| 10 IOPS/GB | Demanding storage workloads - Data intensive workloads created by NoSQL databases, data processing for video, machine learning, and analytics | 10 GB to 300 GB | Up to 3,000 IOPS |
| | | More than 300 GB to 2 TB | 10 IOPS/GB up to 20,000 IOPS |
{: caption="Table 1. IOPS tier profiles and performance levels for each tier" caption-side="top"}

## Custom IOPS profile
{: #custom}

Custom IOPS is a good option when you have well-defined performance requirements that do not fall within a predefined IOPS tier. You can customize the IOPS by specifying the total IOPS for the volume within the range for its volume size. You can provision volumes with 100 IOPS to 20,000 IOPS.

Table 2 shows the available IOPS ranges based on volume size.

| Volume size (GB) | IOPS range |
|-------------|--------------|
| 10 -39   | 100 - 1,000 |
| 40 - 79 | 100 -2,000 |
| 80 - 99 | 100 - 4,000 |
| 100 - 499 | 100 - 6,000 |
| 500 - 999 | 100 - 10,000 |
| 1,000 - 1,999 | 100 - 20,000 |
{: caption="Table 2. Available IOPS based on volume size" caption-side="top"}

## How virtual server profiles relate to storage profiles
{: #vsi-profiles-relate-to-storage}

Virtual server profiles are a combination of vCPU and RAM that can be instantiated quickly to start a virtual server instance. You select from [three families of profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)
based on your workload requirements.  These requirements can range from common workloads to CPU-intensive or memory-intensive workloads.

Similarly, storage profiles (IOPS tiers or custom) provide a range of capacity and performance for secondary volumes.  By default, a
100 GB primary boot volume is created when you create a virtual server instance. You can also create and attach secondary volumes.
When you create a secondary data volume as part of instance creation, you select a storage profile that best meets your storage
requirements for your compute workloads. In general, as your compute requirements increase, you need higher IOPS performance.  Table 3 shows this relationship.

| IOPS tier storage profile | Virtual server profile |
|-----------------|------------------------|
| 3 IOPS/GB       | [Balanced](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) for common workloads |
| 5 IOPS/GB       | [Compute](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) for intensive CPU demands |
| 10 IOPS/GB      | [Memory](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) for memory-intensive workloads |
{: caption="Table 3. Relationship of block storage profiles to virtual server profiles" caption-side="top"}

## Viewing IOPS profiles
{: #view-iops-profiles}

You can view available IOPS profiles the {{site.data.keyword.cloud_notm}} console, CLI, or API.

### Using the IBM Cloud console
{: using-console-iops-profile}

 When you [create a block storage volume from the {{site.data.keyword.cloud_notm}} console](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), select **Tiers** from the drop-down menu.

 Alternately, select **Custom** and then select an IOPS value within the range for that volume size. Click the storage size link to see a table of size and IOPS ranges.

 ### Using the CLI
 {: using-cli-iops-profiles}

 To view the list of available profiles by using the CLI, run the following command:
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### Using the API
{: using-api-iops-profiles}

The following cURL API request retrieves all volume profiles.

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## Related Information

For information about Balanced, Compute, and Memory profiles for {{site.data.keyword.vsi_is_short}}, see [Profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).
