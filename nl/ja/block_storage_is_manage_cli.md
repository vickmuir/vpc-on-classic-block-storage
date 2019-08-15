---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# CLI を使用したブロック・ストレージ・ボリュームの管理
{: #managing-block-storage-cli}

コマンド・ライン・インターフェース (CLI) から {{site.data.keyword.block_storage_is_short}} を管理します。ボリューム名の更新、ボリューム接続の更新、ボリュームのデタッチ、またはボリュームの削除を行います。{:shortdesc}

## 始めに
{: #before-managing-block-storage-cli}

1. 以下の CLI プラグインをダウンロード、インストール、初期化したことを確認します。
    * {{site.data.keyword.cloud_notm}} CLI
    * インフラストラクチャー・サービス・プラグイン

   詳しくは、[{{site.data.keyword.cloud_notm}}CLI for VPC リファレンス](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)を参照してください。
   
   初めて vpc-infrastructure プラグインをインストールするときは、`ibmcloud is target --gen 1` のようにターゲット世代を gen 1 に設定する必要があります。
{:important}
   
2. [{{site.data.keyword.vpc_short}} がすでに作成されている](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)ことを確認します。

## ボリュームの名前の更新
{: #update-vol-name}

ボリューム名を変更するには、ボリューム名またはボリューム ID のいずれかを指定してから、新しい名前を示します。

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

例:

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

## CLI を使用したボリューム接続の更新
{: #update-vol-name-cli}

`instance-volume-attachment-update` コマンドを使用して、ボリューム接続名を更新し、デフォルトの自動削除設定を変更することができます。

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

`--name` パラメーターを使用して、ボリューム接続の新しい名前を指定します。

インスタンスを削除するとそれに接続されているボリュームも自動的に削除されるようにするには、`--auto-delete true` を指定します。

`Volume Attachment Instance Reference` の詳細を示す例:

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## CLI を使用したボリュームの切り離し
{: #detach-vol-attachment-cli}

`instance-volume-attachment-detach` コマンドを使用して、インスタンスからボリュームを切り離し、ボリューム接続を削除します。 ブロック・ストレージ・ボリュームは削除されません。後で[別のインスタンスに接続](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)できます。

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## CLI を使用したブロック・ストレージ・ボリュームの削除
{: #delete-vol-cli}

`volume-delete` コマンドを使用して、ボリューム ID を指定してブロック・ストレージ・ボリュームを削除します。

**注:** アクティブなブロック・ストレージ・ボリュームを削除することはできません。 まず、[仮想サーバーから切り離す](#detach-vol-attachment-cli)必要があります。

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

例:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

{{site.data.keyword.cloud}} コンソールを使用してブロック・ストレージ・ボリュームを管理する場合、 詳しくは、[ブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)を参照してください。
{:tip}

## 次のステップ
{: #next-step-managing-block-storage-cli}

[CLI を使用してさらにボリュームを作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)します。

既存のブロック・ストレージ・ボリュームに関する問題は、ユーザー自身がトラブルシューティングして解決できる場合があります。 詳しくは、[ブロック・ストレージのトラブルシューティング](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)を参照してください。
