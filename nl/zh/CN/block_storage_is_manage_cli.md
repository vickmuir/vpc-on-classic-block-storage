---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 使用 CLI 管理块存储卷
{: #managing-block-storage-cli}

这些信息适用于经典基础架构环境中的 {{site.data.keyword.cloud}} Virtual Private Cloud。
{: important}

## 开始之前
{: #before-managing-block-storage-cli}

确保下载、安装并初始化以下 CLI 插件：

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} 区域 API CLI

有关更多信息，请参阅 [IBM Cloud CLI for VPC 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)中的先决条件。

## 更新卷名
{: #update-vol-name}

要更改卷名，请指定卷名或卷标识，然后指示新名称。

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

示例：

```bash
$ ibmcloud is volume-update 933c8781-f7f5-4a8f-8a2d-3bfc711788ee --name demo-volume-update
Updating volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount 01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo-volume-update
Capacity                                100
IOPS                                    1000
Profile                                 5iops-tier
Encryption                              -
Encryption                              provider managed
Status                                  available
Created                                 2019-05-20 10:09:28
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Zone                                    us-south-2
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Volume Attachment Instance Reference    none
```
{: screen}

## 使用 CLI 更新卷连接
{: #update-vol-name-cli}

可以使用 `instance-volume-attachment-update` 命令来更新卷连接名称，并更改缺省自动删除设置。

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

使用 `--name` 参数为卷连接指定新名称。

指定 `--auto-delete true` 以在删除卷连接到的实例时自动删除卷。

显示 `Volume Attachment Instance Reference` 的详细信息的示例：

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## 使用 CLI 拆离卷
{: #detach-vol-attachment-cli}

使用 `instance-volume-attachment-detach` 命令从实例拆离卷，并删除卷连接。这不会删除块存储卷；日后可以[将卷连接到其他实例](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## 使用 CLI 删除块存储卷
{: #delete-vol-cli}

使用 `volume-delete` 命令并指定卷标识可删除块存储卷。

**注：**不能删除活动块存储卷。必须先[从虚拟服务器拆离卷](#detach-vol-attachment-cli)。

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

示例：

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

您希望使用 {{site.data.keyword.cloud}} 控制台来管理块存储卷？有关更多信息，请参阅[管理块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)。
{:tip}

## 后续步骤
{: #next-step-managing-block-storage-cli}

[使用 CLI 创建更多卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)。

对于现有块存储卷发生的问题，您可能可以自行进行故障诊断并解决问题。有关更多信息，请参阅[有关块存储器的故障诊断](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)。
