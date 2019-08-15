---

copyright:
  years: 2019
lastupdated: "2019-07-11"

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

# UI を使用したブロック・ストレージ・ボリュームの管理
{: #managing-block-storage}

UI から {{site.data.keyword.block_storage_is_short}} を管理します。仮想サーバー・インスタンスからのボリュームの切り離し、あるインスタンスから別のインスタンスへのボリュームの転送、以前に接続されたボリュームの接続、ボリューム名の変更、自動ボリューム削除の設定、手動によるボリュームの削除、またはボリュームへのアクセス権限の割り当てを行います。
{:shortdesc}

## 仮想サーバー・インスタンスからのブロック・ストレージ・ボリュームの切り離し
{: #detach}

仮想サーバー・インスタンスに現在接続されているブロック・ストレージ・ボリュームを切り離すことができます。  切り離しによってボリュームが解放され、別のインスタンスが使用できるようになります。

ボリュームを切り離すには、以下のようにします。

1. すべてのブロック・ストレージ・ボリュームのリストにナビゲートします。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ (Block storage)」**に移動します。
1. ボリュームを見つけて、テーブル行の末尾にある省略符号 (...) をクリックします。 コンテキスト・メニューが表示されます。
1. メニューから、**「インスタンスから切り離し」**をクリックします。
1. ポップアップで**「インスタンスの切り離し (Detach instance)」**をクリックして確定します。

あるいは、すべてのブロック・ストレージ・ボリュームのリストで個別のボリュームをクリックし、そのボリュームの**「ボリューム詳細」**ページにナビゲートします。 **「接続済みインスタンス」**で、仮想サーバー・インスタンスの横にある負符号をクリックして、そのインスタンスからボリュームを切り離します。

## ある仮想サーバー・インスタンスから別の仮想サーバー・インスタンスにブロック・ストレージ・ボリュームを移転する
{: #transfer}

ブロック・ストレージ・ボリュームを別の仮想サーバー・インスタンスに移転するには、以下のようにします。

1. [ボリュームをその仮想サーバー・インスタンスから切り離します](#detach)。
1. ボリュームの移転先となる仮想サーバー・インスタンスにナビゲートします。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「コンピュート」>「Virtual Server インスタンス」**に移動します。
1. リストから仮想サーバーを選択します。
1. 「接続済みストレージ・ボリューム (Attached Storage volumes)」で、ボリュームを追加するための正符号をクリックします。 すべてのブロック・ストレージ・ボリュームが表示されます。
1. ボリュームのリストから、前に切り離したボリュームを選択します。

## 以前接続されていたブロック・ストレージ・ボリュームの接続
{: #reattach}

新しい仮想サーバー・インスタンスを作成すると、デフォルトでブロック・ストレージ・ボリュームが接続されます。  インスタンスからボリュームを切り離しても、そのボリュームは未接続ボリュームとして存在し、[すべてのブロック・ストレージ・ボリューム](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)のリストに表示されます。 ブロック・ストレージ・ボリュームのリストから別のイメージに接続できます。

1. すべてのブロック・ストレージ・ボリュームのリストにナビゲートします。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ (Block storage)」**に移動します。
1. ボリュームを見つけて、テーブル行の末尾にある省略符号 (...) をクリックします。 コンテキスト・メニューが表示されます。
1. メニューから、**「インスタンスに接続」**をクリックします。
1. 使用可能な仮想サーバー・インスタンスを選択します。
1. 選択内容を確認します。

## ブロック・ストレージ・ボリュームの名前変更
{: #rename}

既存のボリュームの名前を変更して、より分かりやすい名前にすることができます。

1. すべてのブロック・ストレージ・ボリュームのリストにナビゲートします。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ (Block storage)」**に移動します。
1. ボリュームを見つけ、ボリュームの名前をクリックして「ボリューム詳細」ページに移動します。
1. ボリューム名の後にある鉛筆アイコンをクリックし、ボリューム名を編集します。
1. 編集内容を確認します。

## ブロック・ストレージ・ボリュームの削除
{: #delete}

ブロック・ストレージ・ボリュームを削除すると、そのデータも完全に削除されます。 ボリュームは復元できません。

アクティブなブロック・ストレージ・ボリュームを削除することはできません。 ボリュームを削除するには、まず仮想サーバーから[切り離し](#detach)、次に以下の手順を実行します。

1. すべてのブロック・ストレージ・ボリュームのリストにナビゲートします。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「ストレージ」>「ブロック・ストレージ (Block storage)」**に移動します。
1. 削除するボリュームを見つけて、テーブル行の末尾にある省略符号をクリックします。 コンテキスト・メニューが表示されます。
1. メニューから、**「削除」**をクリックします。
1. 削除内容を確認します。

## ブロック・ストレージ・データ・ボリュームの自動削除
{: #auto-delete}

自動削除機能を使用すると、インスタンスを削除したらそれに接続されているブロック・ストレージ・データ・ボリュームも自動的に削除されるようにすることができます。 この機能はブート・ボリュームには適用されません。また、デフォルトでは無効になっています。

インスタンスに接続されている既存のブロック・ストレージ・ボリュームの自動削除を有効にするには、以下の手順を実行します。

1. ボリュームが接続されている仮想サーバー・インスタンスを見つけます。 Virtual Private Cloud の [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「コンピュート」>「Virtual Server インスタンス」**に移動します。
1. **「接続済みブロック・ストレージ・ボリューム」**で、ボリュームを選択します。
1. ポップアップ・メニューで、有効にするための「自動削除」ボタンをクリックします。
1. 選択内容を確認します。

あるいは、ブロック・ストレージ・ボリュームのリストからボリュームを選択することから始めます (**「ストレージ」>「ブロック・ストレージ (Block storage)」**)。

インスタンスの作成時に新規ボリュームの自動削除を有効にするには、[新規インスタンスの作成時にブロック・ストレージ・ボリュームを作成して接続する](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)を参照してください。

## ブロック・ストレージ・ボリュームに対するアクセス権限の割り当て
{: #assign-volume-access}

管理者特権を持つユーザーは、{{site.data.keyword.block_storage_is_short}} サービスに対するボリューム・レベルのユーザー・アクセス権限を割り当てることができます。 次の表は、[ID およびアクセス権の管理 (IAM) UI](/docs/iam?topic=iam-account_setup#assigning-access) で指定する必要がある情報を示しています。

| IAM フィールド | アクション |
|--------|-------------|
| サービス | **「インフラストラクチャー・サービス (Infrastructure Services)」**を選択します |
| リソース・タイプ | **「Block Storage for VPC」**を選択します |
| ボリューム ID | 特定のボリュームに対するアクセス権限を割り当てるための [ボリューム ID](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) を入力します |
| 役割の選択 | プラットフォーム・アクセス役割を割り当てます (通常は「オペレーター」) |
{: caption="表 1. IAM の情報" caption-side="top"}

詳しくは、[アクセス権限を割り当てるためのベスト・プラクティス](/docs/iam?topic=iam-account_setup#account_setup)を参照してください。 アカウントへのユーザーの招待や Cloud IAM アクセス権限の割り当てを含め、IAM プロセス全体については、[IAM 入門チュートリアル](/docs/iam?topic=iam-getstarted#getstarted)を参照してください。

## ブロック・ストレージ・ボリューム状況
{: #status}

次の表は、ブロック・ストレージ・ボリュームを作成、表示、または管理しているときに表示される可能性がある状況を示しています。

| 状況 | 意味 |
|--------|-------------|
| 使用可能 | ボリュームは正常に取得されました |
| | ボリュームは使用可能であり、インスタンスに接続できます |
| | 接続済みボリュームはデータに使用可能です
| | ブート・ボリュームが使用可能です |
| 失敗    | ボリューム作成に失敗しました |
| | 地域内のすべてのボリュームは取得できませんでした |
| | 指定されたボリューム ID のボリュームが見つかりませんでした |
| | ボリュームを削除できませんでした |
| 保留中 | ボリュームを作成中です |
| | ボリュームをインスタンスに接続中です |
| 削除待ち | ボリュームを削除中です |
{: caption="表 2. ブロック・ストレージの状況" caption-side="top"}

CLI を使用してブロック・ストレージ・ボリュームを管理する場合、 詳しくは、[CLI を使用したブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli) を参照してください。
{: tip}

## 次のステップ
{: #next-step-managing-block-storage}

[追加のボリュームを作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)できます。

既存のブロック・ストレージ・ボリュームに関する問題は、ユーザー自身がトラブルシューティングして解決できる場合があります。 詳しくは、[ブロック・ストレージのトラブルシューティング](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)を参照してください。
