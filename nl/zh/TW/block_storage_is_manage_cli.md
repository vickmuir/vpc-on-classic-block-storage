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


# 使用 CLI 管理區塊儲存空間磁區
{: #managing-block-storage-cli}

此資訊適用於「標準基礎架構」環境中的 {{site.data.keyword.cloud}} Virtual Private Cloud。
{: important}

## 在開始之前
{: #before-managing-block-storage-cli}

請確定您已下載、安裝及起始設定下列 CLI 外掛程式：

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} 區域 API CLI

如需相關資訊，請參閱 [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference) 中的必要條件。

## 更新磁區的名稱
{: #update-vol-name}

若要變更磁區名稱，請指定磁區名稱或 ID，然後指出新名稱。

```bash
ibmcloud 是 volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

範例：

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

## 使用 CLI 更新磁區連接
{: #update-vol-name-cli}

您可以更新磁區連接名稱，並使用 `instance-volume-attachment-update` 指令變更預設自動刪除設定。

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

使用 `--name` 參數，並為磁區連接指定新名稱。

當您刪除磁區所連接的實例時，請指定 `--auto-delete true`，以自動刪除磁區。

範例顯示 `Volume Attachment Instance Reference` 的詳細資料：

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## 使用 CLI 分離磁區
{: #detach-vol-attachment-cli}

使用 `instance-volume-attachment-detach` 指令從實例中分離磁區並刪除磁區連接。不會刪除區塊儲存空間磁區；之後您可以[將它連接到另一個實例](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## 使用 CLI 刪除區塊儲存空間磁區
{: #delete-vol-cli}

使用 `volume-delete` 指令，並指定磁區 ID 來刪除區塊儲存空間磁區。

**附註：**您無法刪除作用中的區塊儲存空間磁區。您必須先[將它從虛擬伺服器分離](#detach-vol-attachment-cli)。

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

範例：

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

您偏好使用 {{site.data.keyword.cloud}} 主控台來管理區塊儲存空間磁區嗎？如需相關資訊，請參閱[管理區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)。
{:tip}

## 下一步
{: #next-step-managing-block-storage-cli}

[使用 CLI 來建立更多磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)。

對於現有區塊儲存空間磁區的問題，您可能可以自行疑難排解及修正問題。如需相關資訊，請參閱[區塊儲存空間的疑難排解](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)。
