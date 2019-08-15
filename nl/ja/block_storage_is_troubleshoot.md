---

copyright:
  years: 2019
lastupdated: "2018-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot

subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# {{site.data.keyword.block_storage_is_short}} のトラブルシューティング
{: #troubleshoot}

{{site.data.keyword.block_storage_is_short}}を作成したり管理したりするときに、問題が発生することがあります。多くの場合、いくつかの簡単なステップに従うことで、復旧できます。 問題、症状、考えられる原因、解決方法について、以下のセクションで説明します。
{:shortdesc}

## 指定した地域内のボリュームを取得できない
{: #troubleshoot-topic-1}

特定の地域のブロック・ストレージ・ボリュームに関する情報を取得できなかった。
{: tsSymptoms}

以下のいずれかの原因が該当する可能性があります。

* UI 出力または CLI 出力のいずれかでボリュームの名前と情報が欠落している。
* ご使用の地域以外の地域内のボリュームにアクセスしようとしている可能性もある。
* 第 2 世代のボリュームにアクセスしようとしている可能性がある。
{: tsCauses}

ボリュームが仮想サーバー・インスタンスから切り離されておらず、削除されていないことを確認してください。 以下のようにして、すべての仮想サーバー・インスタンスのリストから、ボリュームを最後に接続したインスタンスを探します。

1. [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}/vpc){: external}で、**メニュー・アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) >「コンピュート」>「仮想サーバー・インスタンス」**にナビゲートします。

1. すべての仮想サーバーのリストから仮想サーバー・インスタンスを選択します。

ボリュームが予期したとおりに接続されておらず、ボリュームのリストに表示されない場合、そのボリュームは削除されていることが考えられます。  ボリュームを削除するとそのデータは完全に削除されるため、ボリュームを復元することはできません。  

CLI を使用する場合は、ボリュームを表示するための正しい構文を入力したことを確認してください。 [CLI を使用したすべてのブロック・ストレージ・ボリュームの表示](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)を参照してください。 正しいリソース・グループまたはゾーンを指定したことを確認してください。
{: tsResolve}

## 名前または ID を指定してボリュームを削除できない
{: #troubleshoot-topic-2}

名前または ID を指定してブロック・ストレージ・ボリュームを削除できない。
{: tsSymptoms}

ボリューム名およびボリューム ID が受け入れられません。
{: tsCauses}

ボリューム名またはボリューム ID が正しいこと、およびボリュームが仮想サーバー・インスタンスに接続されていないことを確認してください。 また、ボリュームが保留状態でないことを確認してください。
{: tsResolve}
