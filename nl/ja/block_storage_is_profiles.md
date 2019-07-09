---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}


# プロファイル
{: #block-storage-profiles}

{{site.data.keyword.cloud_notm}} コンソール、CLI、または API を使用して {{site.data.keyword.block_storage_is_short}} 2 次ボリュームをプロビジョンするときに、ストレージ要件を最も満たす IOPS プロファイルを指定します。プロファイルには、3 つの事前定義 IOPS ティア・プロファイルとカスタム IOPS プロファイルがあります。IOPS ティアで提供される IOPS/GB のパフォーマンスは、最大 2 TB の容量のボリュームまで保証されます。カスタム IOPS プロファイルを指定して、特定の範囲内でボリューム容量と IOPS を定義することもできます。

## ティア IOPS プロファイル
{: #tiers}

ブロック・ストレージでは 3 つの IOPS ティアが事前定義されており、その中から選択することによって、コンピュート・ワークロードに応じて最適パフォーマンスを指定し、ボトルネックを回避することができます。次の表に示すように、IOPS が保証されたボリュームをアベイラビリティー・ゾーンにプロビジョンできます。

| IOPS ティア | ワークロード | ボリューム・サイズ | 最大 IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | 汎用ワークロード - Web アプリケーション用の小さなデータベースをホストするワークロード、またはハイパーバイザー用の仮想マシン・ディスク・イメージを保管するワークロード | 10 GB から 1 TB | 最大 3,000 IOPS まで |
| | | 1 TB 超 2 TB 以下 | 3 IOPS/GB (最大 6,000 IOPS まで) |
| 5 IOPS/GB | 高入出力集中型ワークロード -トランザクション・データベースや他のパフォーマンス依存型データベースなど、多数のアクティブ・データを特徴とするワークロード | 10 GB から 600 GB | 最大 3,000 IOPS まで |
| | | 600 GB 超 2 TB 以下 | 5 IOPS/GB (最大 10,000 IOPS まで) |
| 10 IOPS/GB | 要求の厳しいストレージ・ワークロード - NoSQL データベース、ビデオ用データ処理、機械学習、および分析によって作成されるデータ集中型ワークロード | 10 GB から 300 GB | 最大 3,000 IOPS まで |
| | | 300 GB 超 2 TB 以下 | 10 IOPS/GB (最大 20,000 IOPS まで) |
{: caption="表 1. IOPS ティアとパフォーマンス " caption-side="top"}

すべてのブロック・ストレージ IOPS ティアの最大スループットは、16K ブロック・サイズ・ベースで 750 MB/秒です。

## カスタム IOPS プロファイル
{: #custom}

カスタム IOPS は、事前定義された IOPS ティアの範囲に収まらない、明確に定義されたパフォーマンス要件がある場合に適しています。ボリューム・サイズに対応する範囲内でボリュームの合計 IOPS を指定することにより、IOPS をカスタマイズできます。100 IOPS から 20,000 IOPS までのボリュームをプロビジョンできます。

次の表は、ボリューム・サイズに基づいた使用可能な IOPS 範囲を示しています。

| ボリューム・サイズ (GB) | IOPS 範囲 |
|-------------|--------------|
| 10 から 39   | 100 から 1,000 |
| 40 から 79 | 100 から 2,000 |
| 80 から 99 | 100 から 4,000 |
| 100 から 499 | 100 から 6,000 |
| 500 から 999 | 100 から 10,000 |
| 1,000 から 1,999 | 100 から 20,000 |
{: caption="表 2. ボリューム・サイズに基づいた使用可能な IOPS" caption-side="top"}

## 仮想サーバー・プロファイルとストレージ・プロファイルの関係
{: #vsi-profiles-relate-to-storage}

仮想サーバー・プロファイルは、仮想サーバー・インスタンスを開始するために素早くインスタンス化できる vCPU と RAM の組み合わせです。ワークロード要件に基づいて、[3 つプロファイル・ファミリー](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)から選択します。これらの要件の範囲は、一般的ワークロードから CPU 集中型ワークロードやメモリー集中型ワークロードに及びます。  

同様に、ストレージ・プロファイル (IOPS ティアまたはカスタム) は、2 次ボリュームの容量とパフォーマンスの範囲を定めたものです。デフォルトでは、仮想サーバー・インスタンスの作成時に 100 GB の 1 次ブート・ボリュームが作成されます。2 次ボリュームを作成して接続することもできます。  
インスタンス作成の一部として 2 次データ・ボリュームを作成するときに、コンピュート・ワークロードのストレージ要件を最も満たすストレージ・プロファイルを選択します。一般に、コンピュート要件が増すにつれて、必要な IOPS パフォーマンスは高くなります。次の表は、この関係を示しています。

| IOPS ティアのストレージ・プロファイル | 仮想サーバー・プロファイル |
|-----------------|------------------------|
| 3 IOPS/GB       | [平衡型](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) (一般的ワークロードの場合) |
| 5 IOPS/GB       | [コンピュート](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) (集中 CPU 要求の場合) |
| 10 IOPS/GB      | [メモリー](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) (メモリー集中型ワークロードの場合) |

## IOPS プロファイルの表示
{: #view-iops-profiles}

使用可能な IOPS プロファイルを {{site.data.keyword.cloud_notm}} コンソール、CLI、または API で表示できます。

### IBM Cloud コンソールを使用
{: using-console-iops-profile}

 [{{site.data.keyword.cloud_notm}}コンソールからブロック・ストレージ・ボリュームを作成する](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)ときに、ドロップダウン・メニューから**「ティア」**を選択します。

 あるいは、**「カスタム」**を選択してから、そのボリューム・サイズに対応する範囲内の IOPS 値を選択します。ストレージ・サイズのリンクをクリックすると、サイズと IOPS の範囲の表が表示されます。

 ### CLI の使用
 {: using-cli-iops-profiles}

 使用可能なプロファイルのリストを CLI を使用して表示するには、次のコマンドを実行します。
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### API を使用
{: using-api-iops-profiles}

次の cURL API 要求は、すべてのボリューム・プロファイルを取得します。

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## 関連情報

{{site.data.keyword.vsi_is_short}} の平衡型プロファイル、コンピュート・プロファイル、メモリー・プロファイルについては、[プロファイル](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)を参照してください。
