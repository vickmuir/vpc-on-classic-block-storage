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

# {{site.data.keyword.cloud_notm}} 콘솔에서 블록 스토리지 볼륨 작성
{: #creating-block-storage}
[comment]: # (링크된 도움말 항목)

가상 서버 인스턴스 작성 시에 {{site.data.keyword.block_storage_is_short}} 볼륨을 작성하거나 나중에 인스턴스를 연결하기 위한 독립형 볼륨을 작성할 수 있습니다.
{:shortdesc}

시작하기 전에 [{{site.data.keyword.vpc_short}}를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)했는지 확인하십시오.
{:important}

## 새 인스턴스 작성 시에 블록 스토리지 볼륨 작성 및 연결
{: #create-from-vsi}

1. 인스턴스를 작성하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 컴퓨팅 > 가상 서버 인스턴스 > 새 인스턴스**로 이동하십시오.
1. [가상 서버 인스턴스를 구성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers)하십시오. **연결된 블록 스토리지 볼륨** 아래에서 **새 블록 스토리지 볼륨**을 선택하십시오.
1. 다음 표에 설명된 정보를 입력하십시오.  완료되면 **볼륨 작성**을 클릭하십시오.

| 필드 | 값 |
|-------|-------|
|이름  | 볼륨에 대해 의미 있는 이름(예: 컴퓨팅 또는 워크로드 기능을 설명하는 이름)을 지정하십시오. 영문자와 숫자를 조합하여 입력할 수 있으며, 원하면 나중에 이름을 편집할 수 있습니다. |
| 프로파일 | [티어](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)를 선택하고 IOPS 목록에서 필요한 성능 레벨을 선택하십시오. 성능 요구사항이 사전 정의된 IOPS 티어 내에 속하지 않으면 [사용자 정의](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)를 선택하고 해당 볼륨 크기의 범위 내에서 IOPS 값을 선택하십시오. **스토리지 크기** 링크를 클릭하여 크기와 IOPS 범위의 표를 볼 수 있습니다. |
| 자동 삭제 | 연결된 가상 서버 인스턴스의 삭제 시에 이 볼륨을 자동으로 삭제하려면 이 기능을 사용으로 설정하십시오. 나중에 가상 서버 세부사항 페이지에서 이 설정을 변경할 수 있습니다. |
| IOPS | 티어 프로파일에 대해 3, 5 또는 10 IOPS/GB를 선택하십시오. |
|크기 | 볼륨 크기(GB)를 입력하십시오.  볼륨 크기는 10GB - 2TB 사이일 수 있습니다. |
| 암호화 | 모든 볼륨에서 기본적으로 IBM 관리 키의 암호화가 사용됩니다. **고객 관리**를 선택하고 사용자 고유의 암호화 키를 사용할 수도 있습니다.  전제조건 및 고객 관리 암호화 설정 단계는 [고객 관리 암호화로 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)을 참조하십시오. |
{: caption="표 1. 인스턴스 프로비저닝 시에 지정된 블록 스토리지 볼륨 값" caption-side="top"}

블록 스토리지 볼륨이 작성되어 가상 서버 인스턴스에 연결됩니다. 인스턴스 세부사항 페이지에서 **연결된 블록 스토리지 볼륨** 목록이 업데이트되어 새 볼륨을 표시합니다.

블록 스토리지 볼륨은 한 번에 하나의 가상 서버에만 연결될 수 있습니다. 블록 스토리지 볼륨 요약 페이지의 **연결된 인스턴스** 아래에서 인스턴스 이름을 선택하여 가상 서버 인스턴스에 대한 세부사항을 볼 수 있습니다.

## 독립형 블록 스토리지 볼륨 작성
{: #create-standalone-vol}

가상 서버 프로비저닝과는 별도로 블록 스토리지 볼륨을 작성하고 나중에 인스턴스에 볼륨을 연결할 수 있습니다.

1. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > 블록 스토리지 볼륨**으로 이동하여 **새 볼륨**을 선택하십시오.
1. 아래에 있는 표의 정보를 입력하여 새 블록 스토리지 볼륨을 정의하십시오.
1. 완료되면 **볼륨 작성**을 클릭하십시오. 블록 스토리지 볼륨 페이지로 리턴되며, 여기서 메시지는 볼륨을 작성 중임을 표시합니다. 볼륨이 작성되면 두 번째 메시지가 표시됩니다.
1. 새 볼륨의 세부사항을 보려면 두 번째 메시지의 **리소스 보기** 링크를 선택하여 볼륨 세부사항 페이지로 이동하십시오.

| 필드 |값 |
|-------|-------|
|이름  | 볼륨에 대해 의미 있는 이름을 지정하십시오. 예를 들어, 컴퓨팅 또는 워크로드 기능을 설명하는 이름을 제공하십시오. 최대 40자의 영숫자 문자를 입력할 수 있으며, 나중에 이름을 편집할 수 있습니다. |
| 리소스 그룹 | 리소스 그룹을 지정하십시오. 리소스 그룹은 액세스 제어와 비용 청구 용도로 계정 리소스를 구성하는 데 도움이 됩니다. 리소스 그룹 설정에 대한 정보는 [리소스 그룹의 리소스 구성에 대한 우수 사례](/docs/resources?topic=resources-bp_resourcegroups#setuprgs)를 참조하십시오. |
| 태그 | 리소스를 구성하기 위한 태그를 지정하십시오. 태그는 리소스 목록에서 리소스의 손쉬운 필터링을 위해 리소스에 지정하는 레이블입니다. 태그에 대한 정보는 [태그 관련 작업](/docs/resources?topic=resources-tag)을 참조하십시오. |
| 위치 | VPC에서 상속된 사용자 지역의 가용성 구역(예: US South 1)입니다. |
| 크기 | 볼륨 크기(GB)를 입력하십시오.  볼륨 크기는 10GB - 2TB 사이일 수 있습니다. |
| IOPS | [IOPS 티어](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)를 선택하고 필요한 성능 레벨의 타일을 선택하십시오. |
| 사용자 정의 | 지정한 볼륨의 크기에 따라 해당 볼륨 크기 범위 내에서 IOPS 값을 선택하십시오.  **스토리지 크기** 링크를 클릭하여 크기와 IOPS 범위의 표를 볼 수 있습니다. 자세한 정보는 [사용자 정의 IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)을 참조하십시오. |
| 암호화 | 모든 볼륨에서 기본적으로 IBM 관리 키의 암호화가 사용됩니다. 사용자 고유의 암호화 키를 사용하려면 고객 관리 암호화 옵션을 선택하십시오. 자세한 정보는 [고객 관리 암호화로 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)을 참조하십시오.|
{: caption="표 2. 블록 스토리지 볼륨 정의를 위한 값" caption-side="top"}

CLI를 사용한 블록 스토리지 볼륨 작성을 원하십니까? 자세한 정보는 [CLI를 사용하여 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)을 참조하십시오.
{: tip}

## 다음 단계
{: #next-step-creating-block-storage}

블록 스토리지 볼륨 페이지를 새로 고치면 새 볼륨이 볼륨 목록의 맨 위에 나타납니다. 볼륨 작성에 성공하면 이는 "사용 가능" 상태를 표시합니다. 독립형 볼륨의 경우에는 연결 유형 열이 공백(-)입니다. 테이블 행의 끝에 있는 조치 메뉴(...)는 [인스턴스에 블록 스토리지 볼륨 연결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)에 대한 링크를 제공합니다.

계속해서 블록 스토리지 볼륨을 추가로 작성하거나 기존 볼륨을 관리할 수 있습니다.

* [블록 스토리지 볼륨에 대한 세부사항 보기](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [가상 서버 인스턴스에서 볼륨 분리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [블록 스토리지 볼륨 삭제](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
