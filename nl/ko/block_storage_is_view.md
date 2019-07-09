---

copyright:
  years: 2019
lastupdated: "2019-06-14"

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

# 블록 스토리지 볼륨 세부사항 보기
{: #viewing-block-storage}

블록 스토리지 볼륨에 대한 세부사항이나 모든 볼륨에 대한 요약 정보를 봅니다. 

## 모든 블록 스토리지 볼륨에 대한 정보 보기
{: #viewvols}

블록 스토리지 볼륨의 목록으로 이동하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > VPC용 블록 스토리지 볼륨**으로 이동하십시오. 

기본적으로는 사용자 지역의 모든 리소스 그룹에 대해 블록 스토리지 볼륨이 표시됩니다. 모든 **블록 스토리지 볼륨**의 목록에는 다음 정보가 나타납니다. 

| 필드 |설명 |
|-------|-------------|
|상태 | 모든 행에 대해 기본 필터로 작동하는 볼륨의 상태입니다. 볼륨 상태에 대한 정보는 [블록 스토리지 볼륨 상태](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status)를 참조하십시오. |
|이름 | 개별 볼륨 세부사항을 보려면 볼륨의 이름을 클릭하십시오. |
| 리소스 그룹 |  VPC를 설정할 때 정의된 리소스 그룹입니다. 리소스 그룹은 리소스에 대한 액세스를 관리하지만 비용 청구나 모니터링에는 영향을 주지 않습니다.|
| 위치 | VPC에서 상속된 사용자 지역의 가용성 구역(예: US South 1)입니다. |
|크기 | 지정한 볼륨의 크기(GB)입니다. |
| 최대 IOPS | 범용 IOPS 티어 또는 지정한 사용자 정의 IOPS 값으로 정의된 볼륨에서 사용 가능한 최대 IOPS입니다. |
| 연결 유형 | 데이터(인스턴스에 연결된 2차 볼륨의 경우), 부트(부트 볼륨으로 연결된 경우) 또는 공백(연결되지 않은 볼륨의 경우)입니다. |
| 암호화 | 제공자 관리 또는 [고객 관리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)입니다. |
| 조치(...) | 수행 가능한 컨텍스트 특정 조치의 메뉴를 표시하려면 생략 기호를 클릭하십시오. 예를 들어, 사용 가능한 연결되지 않은 볼륨에는 인스턴스에 연결하거나 볼륨을 삭제하기 위한 메뉴 옵션이 있습니다. |
{: caption="표 1. 모든 볼륨에 대한 세부 사항" caption-side="top"}

기본적으로는 10개의 볼륨이 모든 블록 스토리지 볼륨의 목록에 표시됩니다. 아래로 화살표를 클릭하여 이 기본값을 변경하고 20개 또는 50개 볼륨으로 목록을 늘리십시오. 오른쪽 하단의 모서리에 있는 화살표를 사용하여 다음 페이지로 이동한 후 다시 돌아올 수 있습니다. 

## 블록 스토리지 볼륨에 대한 세부사항 보기
{: #view-vol-details}

블록 스토리지 볼륨에 대한 세부사항을 보려면 모든 블록 스토리지 볼륨의 목록으로 이동하여 볼륨을 선택하십시오. 단일 볼륨의 경우에는 다음 정보가 나타납니다. 

| 필드 |설명 |
|-------|-------------|
|이름  | 볼륨을 작성할 때 지정한 볼륨의 이름입니다. 연필 아이콘을 클릭하여 볼륨 이름을 편집하십시오.|
| 리소스 그룹 |  VPC를 설정할 때 정의된 리소스 그룹입니다. 리소스 그룹은 리소스에 대한 액세스를 관리하지만 비용 청구나 모니터링에는 영향을 주지 않습니다.|
| 연결 유형 | 데이터(인스턴스에 연결된 2차 볼륨의 경우), 부트(부트 볼륨으로 연결된 경우) 또는 공백(연결되지 않은 볼륨의 경우)입니다. |
| ID | 시스템 생성 볼륨 ID입니다. |
| 작성 날짜 | 볼륨이 작성된 시점의 시스템 생성 날짜입니다. |
| 위치 | 사용자 지역의 가용성 구역입니다. |
|크기 | 지정한 볼륨의 크기입니다. |
| 프로파일 | IOPS 티어 또는 사용자 정의 IOPS 프로파일입니다. |
| 최대 IOPS | 사용자 정의 IOPS에 대해 지정한 값이거나 사전 정의된 IOPS 티어의 최대 IOPS 값입니다. |
| 처리량 | 기가비트/초(Gbps)로 측정된 디스크가 제공할 수 있는 성능입니다. 볼륨 프로파일에 따라 처리량은 IOPS * 16K 블록 크기의 양으로 계산됩니다. |
| 암호화 | 제공자 관리 또는 고객 관리입니다. |
{: caption="표 1. 볼륨 세부사항" caption-side="top"}

가상 서버 인스턴스에 연결된 볼륨은 **볼륨 세부사항** 페이지의 **연결된 인스턴스** 아래에 표시됩니다. [인스턴스에 볼륨을 연결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)할 수도 있습니다.

인스턴스에 연결된 볼륨의 경우에는 인스턴스에 대한 정보로 이동한 후 모든 블록 스토리지 볼륨의 목록으로 돌아올 수도 있습니다. 

## 인스턴스 세부사항의 연결된 블록 스토리지 볼륨 세부사항 보기

**가상 서버 인스턴스 세부사항** 페이지에서 연결된 블록 스토리지 볼륨에 대한 정보를 볼 수 있습니다. 

1. [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 컴퓨팅 > VPC용 가상 서버 인스턴스**로 이동하여 인스턴스를 선택하십시오. 
1. **연결된 블록 스토리지 볼륨** 아래에서 볼륨의 이름을 클릭하여 볼륨 세부사항 페이지로 이동하십시오.

CLI를 사용한 블록 스토리지 볼륨 보기를 원하십니까? 자세한 정보는 [블록 스토리지 볼륨 보기(CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli)를 참조하십시오.
{: tip}

## 다음 단계
{: #next-step-viewing-block-storage}

추가 볼륨을 작성하거나 기존 블록 스토리지 볼륨을 관리하십시오. 

* [IBM Cloud 콘솔에서 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [UI를 사용하여 블록 스토리지 볼륨 관리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
