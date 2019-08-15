---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, block storage volume, volume, volume attachment, virtual server instance, instance

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

# UI を使用したブロック・ストレージ・ボリュームの接続
{: #attaching-block-storage}

UI から仮想サーバー・インスタンス用の {{site.data.keyword.block_storage_is_short}} ボリュームを作成する際には、デフォルトでボリュームはインスタンスに接続されます。ボリュームを切り離すと、そのボリュームは未接続ボリュームとして存在するので、後で再接続できます。 これらの使用可能なボリュームは、[すべてのブロック・ストレージ・ボリューム](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)のリストに表示されます。 別のインスタンスへのボリュームの接続は、すべてのブロック・ストレージ・ボリュームのリストから行ったり、特定のインスタンスに関する詳細を表示する際に行ったりできます。
{:shortdesc}

## ボリューム接続の制限
{: #vol-attach-limits}

1 つの仮想サーバー・インスタンスに一度に 1 つのブロック・ストレージ・ボリュームしか接続できませんが、以下の制限のもとで、複数の異なるブロック・ストレージ・ボリュームを単一のインスタンスに接続できます。

* 仮想 CPU が 4 つ未満のインスタンスは、最大 4 つまでのブロック・ストレージ 2 次ボリュームと、さらにブート・ボリュームを接続できます。
* インスタンスの仮想 CPU が 4 つ以上の場合は、最大 12 つまでのブロック・ストレージ 2 次ボリュームと、さらにブート・ボリュームを接続できます。

## ブロック・ストレージ・ボリュームの仮想サーバー・インスタンスへの接続
{: #attach}

すべてのブロック・ストレージ・ボリュームのリストから、以下のステップを実行します。

1. Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ (Block storage)」**に移動します。
1. ボリュームのリストで、使用可能な未接続ボリュームの行の末尾にある省略符号をクリックします。  コンテキスト固有のアクション・メニューが表示されます。
1. **「インスタンスに接続」**を選択します。
1. 使用可能なリソースのリストからコンピュート・リソース (仮想サーバー・インスタンス) を選択し、**「接続」**をクリックします。
1. ボリュームをイメージに接続していることを示すメッセージが、ボリューム詳細ページに表示されます。  完了すると、イメージ名が**「接続済みインスタンス」**の下に表示されます。

仮想サーバー・インスタンスの詳細のページからブロック・ストレージ・ボリュームを接続することもできます。

1. Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「コンピュート」>「Virtual Server インスタンス」**に移動します。
1. すべての仮想サーバー・インスタンスのリストからインスタンスを選択します。 接続済みのブロック・ストレージ・ボリュームがある場合は、**「接続済みブロック・ストレージ・ボリューム」**の下にリストされます。
1. **「ボリュームの接続」**を選択します。
1. 使用可能なリソースのリストからボリュームを選択して、**「接続」**をクリックします。 ボリュームを接続していることを示すメッセージが、インスタンスの詳細ページに表示されます。  完了すると、**「接続済みブロック・ストレージ・ボリューム」**リストが更新され、新しいボリュームが組み込まれます。

CLI を使用してブロック・ストレージ・ボリュームを手動で接続することもできます。 詳しくは、[CLI を使用したブロック・ストレージ・ボリュームの接続](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)を参照してください。
{: tip}

## 次のステップ
{: #next-step-attaching-block-storage}

追加ボリュームを作成し、既存のボリュームを管理します。 以下の情報を参照してください。

* [IBM Cloud コンソールでのブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [UI を使用したブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
