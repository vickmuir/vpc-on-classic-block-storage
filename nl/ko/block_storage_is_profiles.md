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


# 프로파일
{: #block-storage-profiles}

{{site.data.keyword.cloud_notm}} 콘솔, CLI 또는 API를 사용하여 {{site.data.keyword.block_storage_is_short}} 2차 볼륨을 프로비저닝하는 경우, 스토리지 요구사항을 가장 잘 충족하는 IOPS 프로파일을 지정합니다. 프로파일은 세 개의 사전 정의된 IOPS 티어로 또는 사용자 정의 IOPS로 사용 가능합니다. IOPS 티어는 최대 2TB 용량의 볼륨에 대해 보장된 IOPS/GB 성능을 제공합니다. 사용자 정의 IOPS 프로파일을 지정하고 범위 내에서 볼륨 용량과 IOPS를 정의할 수도 있습니다.

## 티어 IOPS 프로파일
{: #tiers}

블록 스토리지는 컴퓨팅 워크로드의 최적 성능 지정과 병목 현상 방지를 위해 선택할 수 있는 세 개의 사전 정의된 IOPS 티어를 제공합니다. 다음 표에 설명된 대로 보장된 IOPS로 가용성 구역의 볼륨을 프로비저닝할 수 있습니다. 

| IOPS 티어 | 워크로드 | 볼륨 크기 | 최대 IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | 범용 워크로드 - 웹 애플리케이션용 소형 데이터베이스를 호스팅하거나 하이퍼바이저의 가상 머신 디스크 이미지를 저장하는 워크로드 | 10GB - 1TB | 최대 3,000 IOPS |
| | | 1TB - 2TB 이상 | 3 IOPS/GB - 최대 6,000 IOPS |
| 5 IOPS/GB | 높은 I/O 집약 워크로드 - 높은 활성 데이터 비중의 특성을 지닌 워크로드(예: 트랜잭션 및 기타 성능에 민감한 데이터베이스) | 10GB - 600GB | 최대 3,000 IOPS |
| | | 600 GB - 2TB 이상 | 5 IOPS/GB - 최대 10,000 IOPS|
| 10 IOPS/GB | 과중한 스토리지 워크로드 - NoSQL 데이터베이스, 동영상용 데이터 처리, 기계 학습 및 분석으로 생성된 데이터 집약 워크로드 | 10GB - 300GB | 최대 3,000 IOPS |
| | | 300GB - 2TB 이상 | 10 IOPS/GB - 최대 20,000 IOPS |
{: caption="표 1. IOPS 티어 및 성능" caption-side="top"}

모든 블록 스토리지 IOPS 티어의 최대 처리량은 16K 블록 크기를 기반으로 750MB/초입니다. 

## 사용자 정의 IOPS 프로파일
{: #custom}

사용자 정의 IOPS는 사전 정의된 IOPS 티어 내에 속하지 않는 잘 정의된 성능 요구사항이 있는 경우에 적합한 옵션입니다. 볼륨 크기 범위 내의 볼륨에 대한 총 IOPS를 지정하여 IOPS를 사용자 정의할 수 있습니다. 100 IOPS - 20,000 IOPS로 볼륨을 프로비저닝할 수 있습니다. 

다음 표는 볼륨 크기에 따라 사용 가능한 IOPS 범위를 보여줍니다. 

| 볼륨 크기(GB) | IOPS 범위 |
|-------------|--------------|
| 10 -39   | 100 - 1,000 |
| 40 - 79 | 100 -2,000 |
| 80 - 99 | 100 - 4,000 |
| 100 - 499 | 100 - 6,000 |
| 500 - 999 | 100 - 10,000 |
| 1,000 - 1,999 | 100 - 20,000 |
{: caption="표 2. 볼륨 크기에 따라 사용 가능한 IOPS" caption-side="top"}

## 가상 서버 프로파일을 스토리지 프로파일과 연관시키는 방법
{: #vsi-profiles-relate-to-storage}

가상 서버 프로파일은 가상 서버 인스턴스의 시작을 위해 빠르게 인스턴스화가 가능한 vCPU와 RAM의 조합입니다. 워크로드 요구사항을 기반으로 [세 개의 프로파일 제품군](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)에서 선택하십시오. 이러한 요구사항의 범위는 일반 워크로드에서 CPU 집약 또는 메모리 집약 워크로드까지일 수 있습니다.   

이와 유사하게, 스토리지 프로파일(IOPS 티어 또는 사용자 정의)은 2차 볼륨의 용량과 성능 범위를 제공합니다. 기본적으로는 가상 서버 인스턴스 작성 시에 100GB 1차 부트 볼륨이 작성됩니다. 2차 볼륨을 작성하고 연결할 수도 있습니다.  
인스턴스 작성의 일부로서 2차 데이터 볼륨을 작성하는 경우, 컴퓨팅 워크로드의 스토리지 요구사항을 가장 잘 충족하는 스토리지 프로파일을 선택합니다. 일반적으로, 컴퓨팅 요구사항이 증가하면 더 높은 IOPS 성능이 필요합니다. 다음 표에는 이러한 관계가 표시되어 있습니다.

| IOPS 티어 스토리지 프로파일 | 가상 서버 프로파일 |
|-----------------|------------------------|
| 3 IOPS/GB | 일반 워크로드의 경우 [밸런스됨](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) |
| 5 IOPS/GB | CPU 집약 워크로드의 경우 [컴퓨팅](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) |
| 10 IOPS/GB | 메모리 집약 워크로드의 경우 [메모리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) |

## IOPS 프로파일 보기
{: #view-iops-profiles}

{{site.data.keyword.cloud_notm}} 콘솔, CLI 또는 API를 사용하여 사용 가능한 IOPS 프로파일을 볼 수 있습니다. 

### IBM Cloud 콘솔 사용
{: using-console-iops-profile}

 [{{site.data.keyword.cloud_notm}} 콘솔에서 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage) 시에 드롭 다운 메뉴에서 **티어**를 선택하십시오. 

 또는 **사용자 정의**를 선택한 후 해당 볼륨 크기의 범위 내에서 IOPS 값을 선택하십시오. 스토리지 크기 링크를 클릭하여 크기와 IOPS 범위의 표를 볼 수 있습니다. 

 ### CLI 사용
 {: using-cli-iops-profiles}

 CLI를 사용하여 사용 가능한 프로파일의 목록을 보려면 다음 명령을 실행하십시오. 
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### API 사용
{: using-api-iops-profiles}

다음의 cURL API 요청은 모든 볼륨 프로파일을 검색합니다. 

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## 관련 정보

{{site.data.keyword.vsi_is_short}}의 밸런스됨, 컴퓨팅 및 메모리 프로파일에 대한 정보는 [프로파일](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)을 참조하십시오. 
