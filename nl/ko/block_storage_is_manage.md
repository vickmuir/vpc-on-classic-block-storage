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

# UI를 사용하여 블록 스토리지 볼륨 관리
{: #managing-block-storage}

UI에서 {{site.data.keyword.block_storage_is_short}}를 관리하십시오. 가상 서버 인스턴스에서 볼륨을 분리하거나 한 인스턴스에서 다른 인스턴스로 볼륨을 전송하거나 이전에 첨부한 볼륨을 첨부하거나 볼륨의 이름을 바꾸거나 자동 볼륨 삭제를 설정하거나 볼륨을 수동으로 삭제하거나 볼륨에 대한 액세스 권한을 설정하십시오.
{:shortdesc}

## 가상 서버 인스턴스에서 블록 스토리지 볼륨 분리
{: #detach}

현재 가상 서버 인스턴스에 연결된 블록 스토리지 볼륨을 분리할 수 있습니다.  분리를 실행하면 다른 인스턴스가 사용할 수 있도록 볼륨이 해제됩니다.

볼륨을 분리하려면 다음을 수행하십시오.

1. 모든 블록 스토리지 볼륨의 목록으로 이동하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > 스토리지 볼륨**으로 이동하십시오.
1. 볼륨을 찾은 후 테이블 행의 끝에 있는 생략 기호(…)를 클릭하십시오. 컨텍스트 메뉴가 표시됩니다.
1. 메뉴에서 **인스턴스에서 분리**를 클릭하십시오.
1. 팝업에서 **인스턴스 분리**를 클릭하여 이를 확인하십시오.

또는 모든 블록 스토리지 볼륨의 목록에서 개별 볼륨을 클릭하고 해당 볼륨의 **볼륨 세부사항** 페이지로 이동할 수도 있습니다. **연결된 인스턴스** 아래에서 가상 서버 인스턴스 옆의 빼기 부호를 클릭하여 해당 인스턴스에서 볼륨을 분리하십시오.

## 하나의 가상 서버 인스턴스에서 다른 가상 서버 인스턴스로 블록 스토리지 볼륨 전송
{: #transfer}

블록 스토리지 볼륨을 다른 가상 서버 인스턴스로 전송하려면 다음을 수행하십시오.

1. [가상 서버 인스턴스에서 볼륨을 분리](#detach)하십시오.
1. 볼륨이 전송될 가상 서버 인스턴스로 이동하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 컴퓨팅 > 가상 서버 인스턴스**로 이동하십시오. 
1. 목록에서 가상 서버를 선택하십시오.
1. 연결된 스토리지 볼륨 아래에서 더하기 부호를 클릭하여 볼륨을 추가하십시오. 모든 블록 스토리지 볼륨이 표시됩니다.
1. 볼륨 목록에서 이전에 분리한 볼륨을 선택하십시오.

## 이전에 연결된 블록 스토리지 볼륨 연결
{: #reattach}

블록 스토리지 볼륨은 기본적으로 새 가상 서버 인스턴스를 작성할 때 연결됩니다.  인스턴스에서 볼륨을 분리하면 이는 연결되지 않은 볼륨으로 존재하며 [모든 블록 스토리지 볼륨](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)의 목록에 표시됩니다. 블록 스토리지 볼륨 목록에서 다른 이미지에 이를 연결할 수 있습니다.

1. 모든 블록 스토리지 볼륨의 목록으로 이동하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > 스토리지 볼륨**으로 이동하십시오.
1. 볼륨을 찾은 후 테이블 행의 끝에 있는 생략 기호(…)를 클릭하십시오. 컨텍스트 메뉴가 표시됩니다.
1. 메뉴에서 **인스턴스에 연결**을 클릭하십시오.
1. 사용 가능한 가상 서버 인스턴스를 선택하십시오.
1. 선택사항을 확인하십시오.

## 블록 스토리지 볼륨의 이름 바꾸기
{: #rename}

보다 의미가 있도록 기존 볼륨의 이름을 변경할 수 있습니다.

1. 모든 블록 스토리지 볼륨의 목록으로 이동하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > 스토리지 볼륨**으로 이동하십시오.
1. 볼륨을 찾은 후 볼륨의 이름을 클릭하여 볼륨 세부사항 페이지로 이동하십시오.
1. 볼륨 이름 뒤의 연필 아이콘을 클릭하고 볼륨 이름을 편집하십시오.
1. 편집을 확인하십시오.

## 블록 스토리지 볼륨 삭제
{: #delete}

블록 스토리지 볼륨을 삭제하면 해당 데이터가 완전히 제거됩니다. 볼륨을 복원할 수 없습니다.

활성 블록 스토리지 볼륨은 삭제할 수 없습니다. 볼륨을 삭제하려면 우선 가상 서버에서 [이를 분리](#detach)한 후에 다음 단계를 수행하십시오.

1. 모든 블록 스토리지 볼륨의 목록으로 이동하십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > 스토리지 볼륨**으로 이동하십시오.
1. 삭제할 볼륨을 찾은 후 테이블 행의 끝에 있는 생략 기호를 클릭하십시오. 컨텍스트 메뉴가 표시됩니다.
1. 메뉴에서 **삭제**를 클릭하십시오.
1. 삭제를 확인하십시오.

## 블록 스토리지 데이터 볼륨의 자동 삭제
{: #auto-delete}

자동 삭제 기능을 사용하면 연결된 인스턴스를 삭제할 때 블록 스토리지 데이터 볼륨이 자동으로 삭제되도록 지정할 수 있습니다. 이 기능은 부트 볼륨에는 적용되지 않으며 기본적으로 사용되지 않습니다.

인스턴스에 연결된 기존 블록 스토리지 볼륨에 대해 자동 삭제를 사용하려면 다음 단계를 수행하십시오.

1. 볼륨이 연결된 가상 서버 인스턴스를 찾으십시오. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 컴퓨팅 > 가상 서버 인스턴스**로 이동하십시오. 
1. **연결된 블록 스토리지 볼륨** 아래에서 볼륨을 선택하십시오.
1. 팝업 메뉴에서 자동 삭제 단추를 클릭하여 이를 사용으로 설정하십시오.
1. 선택사항을 확인하십시오.

또는 블록 스토리지 볼륨의 목록에서 볼륨을 선택하여 시작하십시오(**스토리지 > 블록 스토리지**).

인스턴스 작성 시에 새 볼륨에서 자동 삭제를 사용으로 설정하려면 [새 인스턴스 작성 시에 블록 스토리지 볼륨 작성 및 연결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)을 참조하십시오.

## 블록 스토리지 볼륨에 대한 액세스 지정
{: #assign-volume-access}

관리자 권한이 있으면 {{site.data.keyword.block_storage_is_short}} 서비스에 대한 볼륨 레벨 사용자 액세스를 지정할 수 있습니다. 다음 표는 [IAM(Identity and Access Management) UI](/docs/iam?topic=iam-account_setup#assigning-access)에서 제공해야 하는 정보를 보여줍니다.

| IAM 필드 | 조치 |
|--------|-------------|
| 서비스 | **인프라 서비스** 선택 |
| 리소스 유형 | **VPC용 블록 스토리지** 선택 |
| 볼륨 ID | 특정 볼륨에 대한 액세스 지정을 위한 [볼륨 ID](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) 입력 |
| 역할 선택 | 플랫폼 액세스 역할(일반적으로 운영자) 지정 |
{: caption="표 1. IAM 정보" caption-side="top"}

자세한 정보는 [액세스 지정에 대한 우수 사례](/docs/iam?topic=iam-account_setup#account_setup)를 참조하십시오. 계정에 사용자 초대와 Cloud IAM 액세스 지정을 포함하는 전체 IAM 프로세스에 대해서는 [IAM 시작하기 튜토리얼](/docs/iam?topic=iam-getstarted#getstarted)을 참조하십시오.

## 블록 스토리지 볼륨 상태
{: #status}

다음 표에는 블록 스토리지 볼륨의 작성, 보기 또는 관리 시에 나타나는 상태가 표시되어 있습니다.

|상태 | 의미 |
|--------|-------------|
| 사용 가능 | 볼륨 검색이 완료됨 |
| | 볼륨이 사용 가능하며 인스턴스에 연결될 수 있음 |
| | 연결된 볼륨을 데이터에 사용할 수 있음
| | 부트 볼륨을 사용할 수 있음 |
| 실패함    | 볼륨 작성에 실패함 |
| | 지역의 모든 볼륨을 검색할 수 없음 |
| | 지정된 볼륨 ID의 볼륨을 찾을 수 없음 |
| | 볼륨을 삭제할 수 없음 |
| 보류 중 | 볼륨을 작성 중임 |
| | 볼륨을 인스턴스에 연결 중임 |
| 삭제 보류 중 | 볼륨을 삭제 중임 |
{: caption="표 2. 블록 스토리지 상태" caption-side="top"}

CLI를 사용한 블록 스토리지 볼륨 관리를 원하십니까? 자세한 정보는 [블록 스토리지 볼륨 관리(CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)를 참조하십시오.
{: tip}

## 다음 단계
{: #next-step-managing-block-storage}

[추가 볼륨을 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)할 수 있습니다.

기존 블록 스토리지 볼륨에 문제가 있으면 문제점을 직접 해결하고 처리할 수 있습니다. 자세한 정보는 [블록 스토리지의 문제점 해결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)을 참조하십시오.
