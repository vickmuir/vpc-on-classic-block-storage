---

Copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# お客様管理の暗号化を使用したブロック・ストレージ・ボリュームの作成
{: #block-storage-encryption}

デフォルトでは、{{site.data.keyword.block_storage_is_short}} ブート・ボリュームおよびデータ・ボリュームは、IBM 管理の暗号化で暗号化されます。それに加え、サポートされる鍵管理サービスを使用してお客様管理の暗号化ボリュームを作成し、カスタマー・ルート鍵を作成またはインポートすることもできます。お客様管理の暗号化は、インスタンスのプロビジョニング時に作成されるブート・ボリュームおよびデータ・ボリューム用のオプションです。さらにスタンドアロン・データ・ボリュームの作成時に、お客様管理の暗号化を指定することもできます。  

## ブロック・ストレージ・ボリュームの鍵管理サービス
{: #key-mgt-services-for-storage}

{{site.data.keyword.keymanagementserviceshort}} と {{site.data.keyword.hscrypto}} (特定の[地域](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)で使用可能) の 2 つの鍵管理サービスを使用できます。{{site.data.keyword.cloud_notm}} データ・センターは、鍵を保護するための専用ハードウェア・セキュリティー・モジュール (HSM) を提供します。以下の表には、各サービスに関する情報が記載されています。

| 鍵管理サービス | HSM 暗号化認証 |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 *レベル 2* 準拠 |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 *レベル 4* 準拠 |

## 前提条件
{: #custom-managed-vol-prereqs}

お客様管理の暗号化を使用するブロック・ストレージ・ボリュームを作成するには、まず鍵管理サービスをプロビジョンし、カスタマー・ルート鍵を作成またはインポートする必要があります。
Cloud Block Storage と鍵管理サービスの間のアクセスを許可する必要もあります。これらの前提条件を満たしたら、お客様管理の暗号化を使用するブロック・ストレージ・ボリュームの作成を開始できます。

以下のステップは {{site.data.keyword.keymanagementserviceshort}} に固有のものですが、全体的な流れは {{site.data.keyword.hscrypto}} にも適用されます。{{site.data.keyword.hscrypto}} を使用している場合は、[{{site.data.keyword.hscrypto}} 情報](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)で対応する手順を参照してください。
{:note}

1. [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) サービスをプロビジョンします。

   新規 {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンスをプロビジョニングすると、ブロック・ストレージ・ボリュームのお客様管理の暗号化に必要な最新の更新が確実に含まれるようになります。2019 年に作成された {{site.data.keyword.keymanagementserviceshort}} インスタンスには、お客様管理の暗号化をサポートするために必要な拡張機能が含まれています。
   {: tip}

2. {{site.data.keyword.keymanagementservicelong_notm}} でカスタマー・ルート鍵 (CRK) を[作成](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)するか[インポート](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys)します。
3. IBM {{site.data.keyword.iamshort}} (IAM) から、**Cloud ブロック・ストレージ** (ソース・サービス) と **{{site.data.keyword.keymanagementserviceshort}}** (ターゲット・サービス) の間の[アクセスを許可](/docs/iam?topic=iam-serviceauth#serviceauth)します。

## UI を使用したお客様管理の暗号化データ・ボリュームの作成
{: #data-vol-encryption-ui}

インスタンスのプロビジョニング時に、またはスタンドアロン・ボリュームとして、新規ブロック・ストレージ・ボリュームを作成するときに、お客様管理の暗号化を指定することができます。

仮想サーバー・インスタンスの作成時に暗号化ボリュームを作成するには、[お客様管理の暗号化を使用した仮想サーバー・インスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok)を参照してください。

スタンドアロン・ボリュームの作成時にお客様管理の暗号化を指定するには、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} コンソールで、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「VPC インフラストラクチャー」>「ストレージ」>「ブロック・ストレージ・ボリューム (Block storage volumes)」**にナビゲートします。
すべてのブロック・ストレージ・ボリュームのリストが表示されます。
1. **「新規ボリューム (New volume)」**を選択します。<!--「新規ブロック・ストレージ・ボリューム (New block storage volume)」ページで、「暗号化」セクションのフィールドを更新します。-->
1. **「新規ブロック・ストレージ・ボリューム (New block storage volume)」**ページで、**「暗号化」**セクションのフィールドを更新します。 詳しくは、以下の表を参照してください。
変更が完了したら、**「ボリュームの作成 (Create Volume)」**をクリックします。

| フィールド | 値 |
| ----- | ----- |
| 暗号化 |_プロバイダー管理_がデフォルトの暗号化モードです。お客様管理の暗号化を使用するには、鍵管理サービス ({{site.data.keyword.keymanagementserviceshort}} または {{site.data.keyword.hscrypto}}) を選択します。鍵管理サービス・インスタンスには、お客様管理の暗号化に使用するカスタマー・ルート鍵を含める必要があります。|
| 暗号化サービス・インスタンス | ご使用のアカウントでプロビジョンされた鍵管理サービス・インスタンスが複数ある場合は、お客様管理の暗号化に使用するカスタマー・ルート鍵が含まれたものを選択します。|
| 鍵名 | ボリュームの暗号化に使用する {{site.data.keyword.keymanagementserviceshort}} インスタンス内のデータ暗号鍵を選択します。|
| 鍵 ID | 選択したデータ暗号鍵に関連付けられている鍵 ID を表示します。 |
{: caption="表 1. お客様管理の暗号化の値" caption-side="top"}

## CLI を使用したお客様管理の暗号化データ・ボリュームの作成
{: #data-vol-encryption-cli}

CLI を使用してお客様管理暗号化を使用するブロック・ストレージ・ボリュームを作成するには、`--encryption-key` パラメーターを指定して `ibmcloud is volume-create` コマンドを指定します。

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

`--encryption-key` パラメーターは、ルート鍵の CRN を取ります。鍵管理サービス・インスタンスのルート鍵の CRN を取得します。詳しくは、[お客様管理の暗号化に関する仮想サーバー・インスタンスの資料](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)を参照してください。CLI を使用したブロック・ストレージ・ボリュームの作成については、[CLI を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)を参照してください。

以下の例は、お客様管理の暗号化を使用して作成された新規ボリュームを示しています。

```bash
$ ibmcloud is volume-create demo_volume custom us-south-1 --iops 1000 --encryption-key abccorp-kp-vpc-2 5437644a-c4b1-447f-9646-b1a2a4df61382
Creating volume demovolume in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          crn:v1:bluemix:public:kms:us-south:a/8d65fb1cf5e99e86dd7229ddef9e5b7b:b1abf7c5-381d-4f34-836e-5db7193250bc:key:fd57250e-908c-4785-a8a5-1f53176bcd2f
Encryption                              customer_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

インスタンスのプロビジョニング中に、お客様管理の暗号化を使用してボリュームを作成することもできます。詳しくは、[CLI を使用した、お客様管理の暗号化によるインスタンスおよびボリュームのプロビジョン](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)を参照してください。

## UI を使用した、お客様管理の暗号化を使用するためのブート・ボリュームの編集

UI からインスタンスを作成するときに、ブート・ボリュームのプロパティーを編集して、お客様管理の暗号化を指定できます。詳しくは、[お客様管理の暗号化を使用するボリュームを使用した仮想サーバー・インスタンスのプロビジョニング](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#provision-byok-ui)を参照してください。
