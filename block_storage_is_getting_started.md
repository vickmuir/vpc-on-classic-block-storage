---

copyright:
  years: 2019
lastupdated: "2019-05-31"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, IBM Cloud, classic, VSI, virtual server

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# Getting started tutorial
{: #block-storage-getting-started}

{{site.data.keyword.block_storage_is_full}} (VPC) provides hypervisor-mounted, high-performance data storage for your virtual server instances (VSIs). You can create block storage volumes when you provision a virtual server instance in a VPC network or create new volumes independent of the VSI lifecycle.
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} is available from the [{{site.data.keyword.cloud_notm}} console ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/vpc) for quick and easy access. You can also provision your block storage volumes by using the [IBM Cloud command-line interface](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference) or by using the [Regional Infrastructure API Service (RIAS)](https://{DomainName}/apidocs/vpc-on-classic).

{{site.data.keyword.block_storage_is_short}} provides features unique to the VPC and is not compatible with the classic infrastructure storage. If you're interested in {{site.data.keyword.blockstoragefull}} on the classic infrastructure, see [Block Storage for IBM Cloud](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).
{:note}

Use the following information to begin creating your block storage volumes.

<table>
  <thead>
    <tr>
      <th>Task</th>
      <th>Details</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Review content that can help with your implementation.</td>
      <td>New to IBM Cloud and Block Storage for VPC? The following sites provide useful information:
        <ul>
          <li>
            <a href="https://ibm.com/cloud-computing">What is IBM Cloud?</a>
          </li>
          <li>
            <a href="https://ibm.com/cloud/get-started">Get started with IBM Cloud</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2. Sign up for IBM Cloud.</td>
      <td>For more information about how to set up your IBM Cloud account, see <a href="https://{DomainName}/docs/account?topic=account-signup#signup">Signing up for IBM Cloud</a>.
      </td>
    </tr>
    <tr>
      <td>3. Determine your storage requirements.</td>
      <td>To learn more about Block Storage for VPC, see <a href="/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about">About Block Storage for VPC</a>.</td>
    </tr>
    <tr>
      <td>4. Size and price your block storage requirements.</td>
      <td>You can select an <a href="/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers">IOPS tier profile</a> for your block storage volume, or specify a <a href="/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom">custom IOPS profile</a>. Use <a href="/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing">Pricing</a> information to help you determine the price of your block storage based on the size and performance you need.</td>
    </tr>
    <tr>
      <td>5. Log in to your IBM Cloud account.</td>
      <td>Access the Block Storage for VPC Order Form from the <a href="https://{DomainName}/catalog">IBM Cloud catalog</a>. Use your IBMid and password</a>.</td>
    </tr>
    <tr>
      <td>6. (Optional) Verify access to the IBM Cloud VPC - Important for creating block storage volumes within a VPC</td>
      <td>To create a block storage volume as part of a VSI provisioning, you must first <a href="/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console">create an IBM Cloud VPC</a>. Skip this step if you want to create a standalone volume outside the VPC. You can later request access to IBM Cloud VPC to access a VSI and attach a block storage volume that you independently created. For more information about the IBM Cloud Virtual Private Cloud, see the <a href="/docs/vpc-on-classic?topic=vpc-on-classic-getting-started">getting started tutorial</a>.</td>
    </tr>
      <td>7. Create your block storage!</td>
      <td>Create block storage volumes by using the <a href="/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage">UI</a>, <a href="/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli">CLI</a>, or <a href="https://cloud.ibm.com/apidocs/vpc-on-classic">API.</a> For more information about using the IBM Cloud Developer tools to install the IBM Cloud CLI, see <a href="/docs/cli?topic=cloud-cli-ibmcloud-cli#overview">Getting started with IBM Cloud Developer tools</a>.</td>
    </tr>
  </tbody>
</table>

## What happens next

After you create block storage, explore more options:

* [View details about the volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Manage your block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
