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


# 使用 CLI 连接块存储卷
{: #attaching-block-storage-cli}

卷连接用于将块存储卷连接到虚拟服务器实例。每个实例可以具有[多个卷连接](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)，但单个卷连接只能将一个卷连接到一个实例。

## 开始之前
{: #before-attaching-block-storage-cli}

确保下载、安装并初始化以下 CLI 插件：

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} 区域 API CLI

有关更多信息，请参阅 [IBM Cloud CLI for VPC 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)中的先决条件。

## 使用 CLI 连接块存储卷
{: #attach-block-storage-cli}

要将卷连接到当前资源组中的虚拟服务器实例，请运行以下命令。

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` 是为卷连接提供的名称，INSTANCE_ID 是 VSI 的标识。

`VOLUME_ID` 指定要连接的卷。

如果希望在删除 VSI 时自动删除卷，请指定 `--auto-delete true`。

要查看可用虚拟服务器实例的列表，请运行 `ibmcloud is instances` 命令。

示例：

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

## 显示连接到虚拟服务器实例的卷的详细信息
{: #show-details-attached-vol}

连接卷后，可以通过在 `instance-volume-attachment` 命令中指定实例标识和卷连接标识来显示详细信息。

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## 列出服务器实例的所有卷连接

使用 `instance-volume-attachments` 命令并指定实例标识以查看实例的所有卷连接。

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

您希望使用 {{site.data.keyword.cloud}} 控制台？有关如何在控制台中连接卷的信息，请参阅[连接块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)。
{:tip}

## 创建卷连接 JSON
{: #volume_attachment_json}

使用 CLI 供应虚拟服务器实例时，如果要在此过程中创建块存储卷，必须指定卷连接 JSON。在命令中指定或作为文件指定的卷连接 JSON 用于定义卷参数。[创建实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)并指定 `--volume-attach` 参数时，可指定卷 JSON。例如，`--volume-attach @/Users/myname/myvolume-attachment_create.json`。

下面是用于定义定制卷的示例卷连接 JSON 文件：

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

## 后续步骤
{: #next-step-attaching-block-storage-cli}

创建其他卷并管理现有卷。请参阅以下信息。

* [使用 CLI 创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [使用 CLI 管理块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
