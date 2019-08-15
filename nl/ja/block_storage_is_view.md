---

copyright:
  years: 2019
lastupdated: "2019-07-24"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

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

# ブロック・ストレージ・ボリュームの詳細の表示
{: #viewing-block-storage}

1 つの {{site.data.keyword.block_storage_is_short}} ボリュームに関する詳細、またはすべてのボリュームに関する要約情報を表示できます。{:shortdesc}

## すべてのブロック・ストレージ・ボリュームに関する情報の表示
{: #viewvols}

ブロック・ストレージ・ボリュームのリストにナビゲートします。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ (Block storage)」**に移動します。

デフォルトでは、地域内のすべてのリソース・グループのブロック・ストレージ・ボリュームが表示されます。  すべての **Block Storage for VPC のボリューム**のリストには、以下の情報が表示されます。

| フィールド | 説明 |
|-------|-------------|
| 状況 | ボリュームの状況。これは、すべての行のデフォルトのフィルターの働きをします。 ボリューム状況については、[ブロック・ストレージ・ボリュームの状況](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status)を参照してください。 |
| 名前 | ボリュームの名前をクリックすると、個別のボリュームの詳細が表示されます。 |
| リソース・グループ | VPC のセットアップ時に定義されるリソース・グループ。リソース・グループを使用すると、アクセス制御や請求処理のためにアカウント・リソースを編成するのに便利です。 詳しくは、『[リソースをリソース・グループに編成するためのベスト・プラクティス](docs/resources?topic=resources-bp_resourcegroups)』を参照してください。|
| ロケーション | VPC から継承される、地域内のアベイラビリティー・ゾーン (米国南部 1 など)。 |
| サイズ | 指定したボリュームのサイズ (GB)。 |
| 最大 IOPS | ボリューム上で使用可能な最大 IOPS。汎用 IOPS ティアまたは指定したカスタム IOPS 値で定義されます。 |
| 接続タイプ | インスタンスに接続している 2 次ボリュームの場合はデータ、ブート・ボリュームとして接続している場合はブート、未接続のボリュームの場合はブランク。 |
| 暗号化 | プロバイダー管理、または[お客様管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)のいずれかです。 |
| アクション (...) | 省略符号をクリックすると、実行できるコンテキスト固有のアクションのメニューが表示されます。  例えば、使用可能な未接続のボリュームには、インスタンスに接続したりボリュームを削除したりするためのメニュー・オプションがあります。 |
{: caption="表 1. すべてのボリュームに関する詳細" caption-side="top"}

デフォルトでは、すべてのブロック・ストレージ・ボリュームのリストには 10 個のボリュームが表示されます。 このデフォルトを変更するには、下矢印をクリックして、リスト内のボリューム数を 20 個または 50 個に増やします。 次のページにナビゲートしたり、再度戻ったりするには、右下隅の矢印を使用します。

## 1 つのブロック・ストレージ・ボリュームに関する詳細の表示
{: #view-vol-details}

1 つのブロック・ストレージ・ボリュームに関する詳細を表示するには、すべてのブロック・ストレージ・ボリュームのリストにナビゲートし、ボリュームを選択します。  単一ボリュームの場合、以下の情報が表示されます。

| フィールド | 説明 |
|-------|-------------|
| 名前  | ボリュームの作成時に指定したボリュームの名前。 ボリューム名を編集するには、鉛筆アイコンをクリックします。 |
| リソース・グループ | VPC のセットアップ時に定義されるリソース・グループ。 リソース・グループは各リソースへのアクセスを管理しますが、請求やモニターには影響しません。 |
| リソース・グループ | ボリュームを関連付けるリソース・グループを選択します。リソース・グループは、アクセスおよび請求処理のためにリソースを編成するのに役立ちます。|
| 接続タイプ | インスタンスに接続している 2 次ボリュームの場合はデータ、ブート・ボリュームとして接続している場合はブート、未接続のボリュームの場合はブランク。 |
| ID | システム生成のボリューム ID。 |
| 作成日 | ボリュームが作成されたシステム生成の日付。 |
| ロケーション | 地域内のアベイラビリティー・ゾーン。 |
| サイズ | 指定したボリュームのサイズ。 |
| プロファイル | IOPS ティアまたはカスタム IOPS のプロファイル。 |
| 最大 IOPS | 事前定義済みの IOPS ティアまたは指定したカスタム IOPS 値の最大 IOPS 値。 |
| スループット | ギガビット/秒 (Gbps) で測定した、ディスクが提供できるパフォーマンス。  ボリューム・プロファイルに基づいて、スループットは IOPS の量 * 16K のブロック・サイズで計算されます。 |
| 暗号化 | プロバイダー管理またはお客様管理のいずれかです。 |
{: caption="表 2. ボリューム詳細" caption-side="top"}

仮想サーバー・インスタンスに接続済みのボリュームは、**「ボリューム詳細」**ページ上の**「接続済みインスタンス (Attached instances)」**の下に表示されます。  自分で[ボリュームをインスタンスに接続](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)することもできます。

インスタンスに接続済みのボリュームの場合、そのインスタンスに関する情報にナビゲートしてから、すべてのブロック・ストレージ・ボリュームのリストに戻ることもできます。

## インスタンスの詳細での接続済みブロック・ストレージ・ボリューム詳細の表示

**「仮想サーバー・インスタンスの詳細 (Virtual server instance details)」**ページから、接続済みのブロック・ストレージ・ボリュームに関する情報を表示できます。

1. [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external} で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「コンピュート」>「Virtual Server インスタンス)」**に進み、インスタンスを選択します。
1. **「接続済みブロック・ストレージ・ボリューム」**の下で、ボリュームの名前をクリックして、そのボリュームの詳細ページに移動します。

CLI を使用してブロック・ストレージ・ボリュームを表示する場合、 詳しくは、[CLI を使用したブロック・ストレージ・ボリュームの表示](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli)を参照してください。
{: tip}

## 次のステップ
{: #next-step-viewing-block-storage}

ボリュームをさらに作成するか、既存のブロック・ストレージ・ボリュームを管理します。

* [IBM Cloud コンソールでのブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [UI を使用したブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
