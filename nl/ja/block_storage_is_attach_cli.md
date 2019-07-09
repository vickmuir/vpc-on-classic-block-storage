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


# CLI を使用したブロック・ストレージ・ボリュームの接続
{: #attaching-block-storage-cli}

ボリューム接続では、ブロック・ストレージ・ボリュームが仮想サーバー・インスタンスに接続されます。各インスタンスには[複数のボリューム接続](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)があってもかまいませんが、単一のボリューム接続では 1 つのボリュームが 1 つのインスタンスに接続されます。

## 始めに
{: #before-attaching-block-storage-cli}

以下の CLI プラグインのダウンロード、インストール、初期化を行ったことを確認します。

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} Regional API CLI

詳しくは、[IBM Cloud CLI for VPC リファレンス](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference) の前提条件を参照してください。

## CLI を使用するブロック・ストレージ・ボリュームの接続
{: #attach-block-storage-cli}

現在のリソース・グループ内の仮想サーバー・インスタンスにボリュームを接続するには、以下のコマンドを実行します。

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` はボリューム接続に指定する名前で、INSTANCE_ID は VSI の ID です。

`VOLUME_ID` は、接続しようとしているボリュームを指定します。

VSI の削除時にボリュームを自動的に削除する場合は、`--auto-delete true` を指定します。

使用可能な仮想サーバー・インスタンスのリストを表示するには、`ibmcloud is instances` コマンドを実行します。

例:

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

## 仮想サーバー・インスタンスに接続しているボリュームの詳細の表示
{: #show-details-attached-vol}

ボリュームを接続し終えたら、`instance-volume-attachment` コマンドでインスタンス ID とボリューム接続 ID を指定して、詳細を表示できます。

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## サーバー・インターフェースのボリューム接続すべてのリスト

`instance-volume-attachments` コマンドを使用して、インスタンス ID を指定すると、そのインスタンスのボリューム接続がすべて表示されます。

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

{{site.data.keyword.cloud}} コンソールの使用をお望みですか? コンソールでのボリュームの接続方法については、[ブロック・ストレージ・ボリュームの接続](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)を参照してください。
{:tip}

## ボリューム接続 JSON の作成
{: #volume_attachment_json}

CLI を使用して仮想サーバー・インスタンスをプロビジョンし、そのプロセスの一部としてブロック・ストレージ・ボリュームを作成する場合は、ボリューム接続 JSON を指定する必要があります。ボリューム接続 JSON は、コマンドで指定するかファイルとして指定し、ボリューム・パラメーターを定義します。[インスタンスを作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)する際に、`--volume-attach` パラメーターを指定する場合は、ボリューム JSON を指定します。例えば、`--volume-attach @/Users/myname/myvolume-attachment_create.json` と指定します。

以下に、カスタム・ボリュームを定義するボリューム接続 JSON ファイルの例を示します。

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

## 次のステップ
{: #next-step-attaching-block-storage-cli}

追加ボリュームを作成し、既存のボリュームを管理します。以下の情報を参照してください。

* [CLI を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [CLI を使用したブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
