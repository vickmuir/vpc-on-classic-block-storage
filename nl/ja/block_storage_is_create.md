---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# {{site.data.keyword.cloud_notm}} コンソールでのブロック・ストレージ・ボリュームの作成
{: #creating-block-storage}
[comment]: # (リンクされたヘルプ・トピック)

仮想サーバー・インスタンスの作成時に{{site.data.keyword.block_storage_is_short}}・ボリュームを作成することも、後でインスタンスに接続するスタンドアロン・ボリュームを作成することもできます。
{:shortdesc}

開始する前に、[{{site.data.keyword.vpc_short}} が作成されている](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)ことを確認してください。
{:important}

## 新規インスタンスの作成時にブロック・ストレージ・ボリュームを作成して接続する
{: #create-from-vsi}

1. インスタンスを作成します。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external} で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「コンピュート」>「Virtual Server インスタンス」>「新規インスタンス」**にナビゲートします。
1. [仮想サーバー・インスタンスを構成します](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers)。 **「接続済みブロック・ストレージ・ボリューム」**で、**「新規ブロック・ストレージ・ボリューム」**を選択します。
1. 以下の表にある情報を入力します。  終了したら、**「ボリュームの作成 (Create volume)」**をクリックします。

| フィールド | 値 |
|-------|-------|
| 名前  | ボリュームに分かりやすい名前を指定します。例えば、コンピュート機能やワークロード機能を説明する名前などです。 英字と数字の組み合わせを入力できます。後で必要に応じて名前を編集することができます。 |
| プロファイル | [「ティア」](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)を選択し、「IOPS」リストから必要なパフォーマンス・レベルを選択します。 パフォーマンス要件が事前定義された IOPS ティアに該当しない場合は、[「カスタム」](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)を選択し、そのボリューム・サイズの範囲内の IOPS 値を選択します。 サイズと IOPS の範囲の表を表示するには、**「ストレージ・サイズ」**リンクをクリックします。 |
| 自動削除 | この機能を有効にすると、接続済みの仮想サーバー・インスタンスが削除されるときに、自動的にこのボリュームを削除します。 この設定は、仮想サーバー詳細ページで後から変更できます。 |
| IOPS | 階層化プロファイルについて、3、5、または 10 IOPS/GB を選択します |
| サイズ | ボリューム・サイズを GB 単位で入力します。  ボリューム・サイズの範囲は 10 GB から 2 TB です。 |
| 暗号化 | IBM 管理鍵による暗号化は、すべてのボリュームでデフォルトで有効になっています。 **「お客様管理」**を選択して、独自の暗号鍵を使用することもできます。  お客様管理の暗号化をセットアップするための前提条件と手順については、[お客様管理の暗号化を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)を参照してください。 |
{: caption="表 1. インスタンスのプロビジョニング時に指定されるブロック・ストレージ・ボリュームの値" caption-side="top"}

ブロック・ストレージ・ボリュームが作成され、仮想サーバー・インスタンスに接続されます。 インスタンスの詳細ページで、**「接続済みブロック・ストレージ・ボリューム」**リストが更新され、新規ボリュームが表示されます。

ブロック・ストレージ・ボリュームは、一度に 1 つの仮想サーバーにしか接続できません。 ブロック・ストレージ・ボリュームの要約ページで、**「接続済みインスタンス」**の下のインスタンス名を選択することにより、仮想サーバー・インスタンスの詳細を表示できます。

## スタンドアロン・ブロック・ストレージ・ボリュームの作成
{: #create-standalone-vol}

仮想サーバーのプロビジョニングに関係なくブロック・ストレージ・ボリュームを作成し、後でそのボリュームをインスタンスに接続することができます。

1. Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ・ボリューム (Block storage volumes)」**にナビゲートし、**「新規ボリューム」**を選択します。
1. 以下の表にある情報を入力して、新規ブロック・ストレージ・ボリュームを定義します。
1. 終了したら、**「ボリュームの作成 (Create volume)」**をクリックします。 「ブロック・ストレージ・ボリューム」ページに戻り、ボリュームが作成中であることを示すメッセージが表示されます。 ボリュームが作成されると、2 つ目のメッセージが表示されます。
1. 新規ボリュームの詳細を表示するには、2 つ目のメッセージの**「リソースの表示」**リンクを選択して、「ボリューム詳細」ページにナビゲートします。

| フィールド | 値 |
|-------|-------|
| 名前  | ボリュームに分かりやすい名前を指定します。 例えば、コンピュート機能やワークロード機能を説明する名前などを指定します。 40 文字までの英数文字を入力でき、名前は後で編集できます。 |
| リソース・グループ | リソース・グループを指定します。 リソース・グループを使用すると、アクセス制御や請求処理のためにアカウント・リソースを編成するのに便利です。 リソース・グループのセットアップについて詳しくは、『[リソースをリソース・グループに編成するためのベスト・プラクティス](/docs/resources?topic=resources-bp_resourcegroups#setuprgs)』を参照してください。 |
| タグ | リソースを編成するためのタグを指定します。 タグは、リソース・リスト内でリソースを簡単にフィルター操作するためにリソースに割り当てるラベルです。 タグについて詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。 |
| ロケーション | VPC から継承された、地域内のアベイラビリティー・ゾーン (例: 米国南部 1)。 |
| サイズ | ボリューム・サイズを GB 単位で入力します。  ボリューム・サイズの範囲は 10 GB から 2 TB です。 |
| IOPS | [「IOPS ティア」](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)を選択し、必要なパフォーマンス・レベルのタイルを選択します。 |
| カスタム | 指定したボリュームのサイズに応じて、そのボリューム・サイズの範囲内の IOPS 値を選択します。  サイズと IOPS の範囲の表を表示するには、**「ストレージ・サイズ」**リンクをクリックします。 詳しくは、[カスタム IOPS プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)を参照してください。 |
| 暗号化 | IBM 管理鍵による暗号化は、すべてのボリュームでデフォルトで有効になっています。 独自の暗号鍵を使用するには、お客様管理の暗号化オプションを選択します。 詳しくは、[お客様管理の暗号化を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)を参照してください。|
{: caption="表 2. ブロック・ストレージ・ボリュームを定義するための値" caption-side="top"}

CLI を使用してブロック・ストレージ・ボリュームを作成する場合、 詳しくは、[CLI を使用したブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)を参照してください。
{: tip}

## 次のステップ
{: #next-step-creating-block-storage}

「ブロック・ストレージ・ボリューム」ページを最新表示すると、ボリュームのリストの先頭に新規ボリュームが表示されます。 ボリュームが正常に作成された場合は、「使用可能」の状況が表示されます。 スタンドアロン・ボリュームの場合は、「接続タイプ」列はブランク (-) です。 表の行の最後にある「アクション」メニュー (...) に、[ブロック・ストレージ・ボリュームをインスタンスに接続する](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)ためのリンクがあります。

さらに多くのブロック・ストレージ・ボリュームを作成することも、既存のボリュームを管理することもできます。

* [ブロック・ストレージ・ボリュームの詳細の表示](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [仮想サーバー・インスタンスからのボリュームの切り離し](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [ブロック・ストレージ・ボリュームの削除](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
