---

copyright:
  years: 2019
lastupdated: "2019-07-03"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# CLI を使用したブロック・ストレージ・ボリュームの表示
{: #viewing-block-storage-cli}

CLI を使用して、1 つの {{site.data.keyword.block_storage_is_short}} ボリュームに関する詳細、またはすべてのボリュームに関する要約情報を表示できます。{:shortdesc}

## 始めに
{: #before-viewing-block-storage-cli}

1. 以下の CLI プラグインをダウンロード、インストール、初期化したことを確認します。
    * {{site.data.keyword.cloud_notm}} CLI
    * インフラストラクチャー・サービス・プラグイン

   詳しくは、[{{site.data.keyword.cloud_notm}}CLI for VPC リファレンス](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)を参照してください。
   
   初めて vpc-infrastructure プラグインをインストールするときは、`ibmcloud is target --gen 1` のようにターゲット世代を gen 1 に設定する必要があります。
{:important}
   
2. [{{site.data.keyword.vpc_short}} がすでに作成されている](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)ことを確認します。

## CLI を使用した 1 つのブロック・ストレージ・ボリュームに関する詳細の表示
{: #viewvol-cli}

1 つのボリュームに関する詳細を表示するには、以下のコマンドを指定します。

```bash
ibmcloud is volume VOLUME_ID [--json]
```

例:

以下の例では、ボリューム ID を使用してボリュームの詳細を表示します。

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

ボリュームを仮想サーバー・インスタンスに接続している場合は、ボリューム接続とインスタンスの名前と ID も表示されます。

## CLI を使用したすべてのブロック・ストレージ・ボリュームの表示
{: #viewall-vol-cli}

すべてのボリュームに関する要約情報をリストするには、以下のコマンドを実行します。

```bash
ibmcloud is volumes [--json]
```

例:

以下の例では、アベイラビリティー・ゾーン内のすべてのリソース・グループに関するすべてのボリュームを表示します。  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

リソース・グループ ID または名前を指定すると、そのリソース・グループに属するボリュームでリストがフィルターに掛けられます。 このパラメーターを省略すると、デフォルトですべてのリソース・グループになります。 特定のアベイラビリティー・ゾーン内のすべてのボリュームを表示することもできます。

デフォルトでは、1 ページあたり最初の 25 個のボリュームが表示されます。

## CLI を使用した 1 つのボリューム接続に関する詳細の表示
{: #viewvol-attachment-cli}

仮想サーバー・インスタンスに対する 1 つのボリューム接続の詳細を表示するには、以下のコマンドを実行します。

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

インスタンス ID とボリューム接続 ID を指定します。  オプションで、JSON 形式で詳細をエクスポートします。

## CLI を使用したすべてのボリューム接続に関する詳細の表示

仮想サーバー・インスタンスに関するすべてのボリューム接続を表示するには、以下のコマンドを実行します。

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## CLI を使用したボリューム・プロファイルの表示
{: #viewvol-profiles-cli}

自分の地域で使用可能なすべてのボリューム・プロファイルをリストするには、以下のコマンドを実行します。

```bash
ibmcloud is volume-profiles [--json]
```

例:

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## CLI を使用した特定のボリューム・プロファイルの表示
{: #viewvol-profile-cli}

自分の地域内の特定のボリューム・プロファイルを表示するには、以下のコマンドを実行します。

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME の値は、10iops-tier、5iops-tier、汎用、カスタムです。

例:

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

{{site.data.keyword.cloud}} コンソールを使用してブロック・ストレージ・ボリュームを表示する場合、 詳しくは、[ブロック・ストレージ・ボリュームの詳細の表示](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)を参照してください。
{: tip}

## 次のステップ
{: #next-step-viewing-block-storage-cli}

ボリュームをさらに作成するか、既存のブロック・ストレージ・ボリュームを管理します。

* [CLI を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [CLI を使用したブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
