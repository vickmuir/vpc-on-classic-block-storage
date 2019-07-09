---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

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

# 블록 스토리지 용량 및 성능
{: #capacity-performance}

워크로드에 대한 최적의 블록 스토리지 볼륨 크기와 성능 레벨을 선택하는 것은 중요합니다. UI 또는 CLI에서 블록 스토리지를 프로비저닝할 때 볼륨 크기와 성능 레벨을 선택할 수 있습니다.

### 용량
{: #block-storage-vpc-capacity}

1GB 증분으로 블록 스토리지 데이터 볼륨당 10GB - 2000GB(2TB)의 용량을 지정할 수 있습니다. 총 볼륨 용량은 [IOPS 프로파일](#iops-profiles)을 선택할 때 결정됩니다. 부트 볼륨은 100GB입니다.

### IOPS 프로파일
{: #iops-profiles}

{{site.data.keyword.block_storage_is_short}} 볼륨을 프로비저닝하는 경우, 스토리지 요구사항을 가장 잘 충족하는 [IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)을 지정합니다. 프로파일은 세 개의 사전 정의된 IOPS 티어로 또는 사용자 정의 IOPS로 사용 가능합니다. [IOPS 티어](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)는 최대 2TB 용량의 볼륨에 대해 보장된 IOPS/GB 성능을 제공합니다. [사용자 정의 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) 프로파일을 지정하고 범위 내에서 볼륨 용량과 IOPS를 정의할 수도 있습니다. {{site.data.keyword.cloud_notm}} 콘솔, CLI 또는 API를 사용하여 프로파일을 지정하십시오. 

## 블록 크기가 성능에 미치는 영향
{: #how-block-size-affects-performance}

IOPS는 50/50 읽기/쓰기 50% 랜덤 워크로드의 16KB 블록 크기를 기반으로 합니다. 16KB 블록은 볼륨에 1회 쓰기와 동일합니다. 기준 처리량은 16KB 블록 크기가 곱해진 IOPS의 양으로 결정됩니다. 지정한 IOPS가 크면 클수록 처리량이 더 늘어납니다. 블록 스토리지 볼륨의 최대 처리량은 750MB/초입니다.

애플리케이션에 대해 선택하는 블록 크기는 스토리지 성능에 직접 영향을 줍니다. 블록 크기가 16KB 미만이면 IOPS 한계가 처리량 한계 이전에 도달됩니다. 이와 반대로 블록 크기가 16KB를 초과하면 처리량 한계가 IOPS 한계 이전에 도달됩니다. 
다음 표는 블록 크기와 IOPS가 처리량에 미치는 영향의 일부 예를 보여줍니다.

| 블록 크기(KB) | IOPS | 처리량(MB/초) |
|-----------------|------|-------------------|
| 4(Linux에 일반적임) | 1,000 |4 |
| 8(Oracle에 일반적임) | 1,000 |8 |
| 16 | 1,000 |16 |
| 32(SQL Server에 일반적임) | 500 |16 |
| 64 | 250 |16 |
| 128 | 128 |16 |
{: caption="표 1은 블록 크기와 IOPS가 처리량에 미치는 영향의 예를 보여줍니다.<br/> 평균 IO 크기 x IOPS = 처리량(MB/초)." caption-side="top"}
