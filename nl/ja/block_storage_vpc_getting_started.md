---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# 入門チュートリアル
{: #getting-started}

このチュートリアルは、Virtual Private Cloud 上で {{site.data.keyword.block_storage_is_short}} ボリュームの作成を開始するのに役立ちます。

## 始めに
{: #block-storage-before-you-begin}

開始するには、まず最初に実装に役立つ内容を確認してください。{{site.data.keyword.cloud}} と {{site.data.keyword.block_storage_is_short}} のご利用は初めてですか? 以下の情報が役立つかもしれません。

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [Block Storage for VPC について](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

{{site.data.keyword.cloud_notm}} アカウントに登録します。詳しくは、[{{site.data.keyword.cloud_notm}} への登録](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}を参照してください。

## ステップ 1 - ストレージ要件の判別
{: #determine-storage-requirements}

ストレージ要件が比較的小さい汎用ワークロードを実行していますか? あるいは、入出力集中型のワークロードで、もっと大きな容量とパフォーマンスが必要ですか? 容量とパフォーマンスを判別する方法について詳しくは、[ブロック・ストレージの容量とパフォーマンス](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance)を参照してください。ストレージ要件に最適な IOPS プロファイル・オプションについては、[プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)も参照してください。 

仮想サーバー・インスタンスも作成しようとしていますか? [仮想サーバー・プロファイルとストレージ・プロファイルの関係](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage)を参照してください。

## ステップ 2 - ブロック・ストレージのサイズと価格設定
{: #size-price-block-storage}

ブロック・ストレージ・ボリュームに関する [IOPS ティア・プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)を選択します。オプションで、事前定義済みの IOPS ティアに該当しない明確なパフォーマンス要件がある場合は、[カスタム IOPS プロファイル](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)を選択します。 

ブロック・ストレージ・ボリュームのサイズとパフォーマンスを選択し終えたら、[料金](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing)の情報を参照して、ボリュームの料金設定と請求方法の把握に役立ててください。

## ステップ 3 - {{site.data.keyword.cloud_notm}} アカウントへのログイン
{: block-storage-log-into-ibm-account}

 [{{site.data.keyword.cloud_notm}} カタログ](https://{DomainName}/catalog){: external} から {{site.data.keyword.block_storage_is_short}} の注文フォームにアクセスします。自分の IBMid とパスワードを使用します。

## ステップ 4 (オプション) - {{site.data.keyword.vpc_short}} に対するアクセスの検証

Virtual Private Cloud 内にボリュームを作成しようとしている場合は、最初に [VPC を作成](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console)する必要があります。VPC の外部にスタンドアロン・ボリュームを作成しようとしている場合は、このステップをスキップします。後で {{site.data.keyword.vpc_short}} へのアクセスを要求して、インスタンスにアクセスし、独自に作成したブロック・ストレージ・ボリュームを接続することができます。{{site.data.keyword.vpc_short}} について詳しくは、VPC の 『[入門チュートリアル](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)』を参照してください。

## ステップ 5 - ブロック・ストレージ・ボリュームの作成

[{{site.data.keyword.cloud_notm}} コンソール (UI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage) で、または [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) または [{{site.data.keyword.vpc_short}} API](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external} を使用して、ボリュームの作成を開始します。IBM Cloud Developer Tools を使用した IBM Cloud CLI のインストールについて詳しくは、[IBM Cloud Developer Tools の入門チュートリアル](/docs/cli?topic=cloud-cli-getting-started) を参照してください。

## 次のステップ
{: #next-step-block-storage-getting-started}

ブロック・ストレージを作成し終えたら、さらに以下のオプションを検討します。

* [ボリュームの詳細の表示](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [ブロック・ストレージ・ボリュームの管理](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
