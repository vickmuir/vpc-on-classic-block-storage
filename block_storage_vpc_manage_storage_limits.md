---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-14"

keywords:

subcollection: vpc-on-classic-block-storage

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="DomainName"}

# Managing volume count and capacity limits
{: #managingstoragelimit-gen1}

{{site.data.keyword.block_storage_is_short}} (Gen 1 Compute) offers block-level data storage volumes that can be attached to an instance as either a boot volume or as a data volume. You can configure up to 300 block storage volumes per account in a region. You can attach several block storage data volumes to a single instance for extra capacity. Capacity for secondary volumes ranges 10 - 2000 GB.
{:shortdesc}

Request more volumes by submitting a support case in the [portal](https://{DomainName}/unifiedsupport/cases/add){: external}.

Provide the following information:

- **Ticket Subject**: Request to Increase VPC Volume Count Limit

- **How many extra volumes are needed and in what region?**
  *For example, your answer might be something similar to "200 volumes in US South".*

- **How many volumes are primary versus secondary?**
  *For example, your answer might be something similar to "50% primary volumes, 50% secondary volumes" or "100 primary volumes, 100 secondary volumes".*

- **How many volumes exceed 1 TB?**
  *For example, your answer might be something similar to "25% exceed 1 TB" or "50 volumes exceed 1 TB".*

- **How many volumes leverage customer-managed encryption?**
  *For example, your answer might be similar to "50% leverages customer-managed encryption" or "100 volumes leverage customer-managed encryption".*

- **Provide an estimate of when you expect or plan to provision all of the requested volumes.**
  *For example, your answer might be something similar to "90 days".*

- **Provide a 90-day forecast of expected average capacity usage of these volumes.**
  *For example, your answer might be something similar to "expect 25 percent to be used in 30 days, 50 percent to be used in 60 days and 75 percent to be used in 90 days".*

Respond to all questions and statements in your request. They are required for processing and approval.
{:important}

You are notified about the update to your limits through the case process.