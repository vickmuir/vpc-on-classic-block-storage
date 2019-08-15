---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM CLoud, VPC, virtual private cloud, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# CLI を使用したブロック・ストレージ・ボリュームの作成
{: #creating-block-storage-cli}

コマンド・ライン・インターフェース (CLI) を使用して {{site.data.keyword.block_storage_is_short}} ボリュームを作成できます。
{:shortdesc}

## 始めに
{: #before-creating-block-storage-cli}

1. 以下の CLI プラグインをダウンロード、インストール、初期化したことを確認します。
    * {{site.data.keyword.cloud_notm}} CLI
    * インフラストラクチャー・サービス・プラグイン

   詳しくは、[{{site.data.keyword.cloud_notm}}CLI for VPC リファレンス](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)を参照してください。
   
   初めて vpc-infrastructure プラグインをインストールするときは、`ibmcloud is target --gen 1` のようにターゲット世代を gen 1 に設定する必要があります。
{:important}
   
2. [{{site.data.keyword.vpc_short}} がすでに作成されている](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)ことを確認します。

## CLI を使用してブロック・ストレージ・ボリュームを作成する
{: #create-vol-cli}

以下のコマンドを実行します。

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

例:

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

容量は M バイト単位で示され、10 から 2,000 GB までの範囲を指定できます。  IOPS の値は、ボリューム・サイズに応じて 1,000 から 20,000 IOPS にすることができます。 IOPS 値を指定しない場合、デフォルトでボリューム・プロファイルごとの有効な構成になります。 詳しくは、[ボリューム・サイズに基づく IOPS 範囲](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)の表を参照してください。

上記の例のボリューム ID は、ブロック・ストレージを仮想サーバー・インスタンスに接続したり、ブロック・ストレージ・ボリュームの詳細を表示したり、ボリュームを削除したりするときに使用されます。

{{site.data.keyword.cloud}} コンソールからブロック・ストレージ・ボリュームを作成する場合、 詳しくは、[ブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)を参照してください。
{: tip}

## 次のステップ
{: #next-step-creating-block-storage-cli}

[ブロック・ストレージ・ボリュームを接続します (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)。
