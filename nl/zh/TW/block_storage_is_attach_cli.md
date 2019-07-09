---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, CLI, block storage volume, volume, volume attachment, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 使用 CLI 連接區塊儲存空間磁區
{: #attaching-block-storage-cli}

磁區連接可將區塊儲存空間磁區連接至虛擬伺服器實例。每個實例都可有[多個磁區連接](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)，但單一磁區連接只會將一個磁區連接至一個實例。

## 在開始之前
{: #before-attaching-block-storage-cli}

請確定您已下載、安裝及起始設定下列 CLI 外掛程式：

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} 地區 API CLI

如需相關資訊，請參閱 [IBM Cloud CLI for VPC 參考資料](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)中的必要條件。

## 使用 CLI 連接區塊儲存空間磁區
{: #attach-block-storage-cli}

若要將磁區連接至現行資源群組中的虛擬伺服器實例，請執行下列指令。

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` 是您提供給磁區連接的名稱，而 INSTANCE_ID 是 VSI 的 ID。

`VOLUME_ID `指定您所附加的磁區。

如果您要在刪除 VSI 時自動刪除磁區，請指定 `--auto-delete true`。

若要查看可用的虛擬伺服器實例清單，請執行 `ibmcloud is instances` 指令。

範例：

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

## 顯示連接至虛擬伺服器實例之磁區的詳細資料
{: #show-details-attached-vol}

在連接磁區之後，您可以在 `instance-volume-attachment` 指令中指定實例 ID 和磁區連接 ID 來顯示詳細資料。

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## 列出伺服器實例的所有磁區連接

請使用 `instance-volume-attachments` 指令，並指定實例 ID 來查看實例的所有磁區連接。

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

您偏好使用 {{site.data.keyword.cloud}} 主控台嗎？如需在主控台中如何連接磁區的相關資訊，請參閱[連接區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)。
{:tip}

## 建立磁區連接 JSON
{: #volume_attachment_json}

當您使用 CLI 佈建虛擬伺服器實例，並在過程中建立區塊儲存空間磁區時，必須指定磁區連接 JSON。指定於指令中或以檔案表示的磁區連接 JSON 會定義磁區參數。當[建立實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)並指定 `--volume-attach `參數時，您可以指定磁區 JSON。例如，`--volume-attach @/Users/myname/myvolume-attachment_create.json`。

以下是定義自訂磁區的磁區連接 JSON 檔案範例：

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

## 下一步
{: #next-step-attaching-block-storage-cli}

建立其他磁區及管理現有磁區。請參閱下列資訊。

* [使用 CLI 建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [使用 CLI 管理區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
