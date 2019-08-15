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

# {{site.data.keyword.block_storage_is_short}} 문제점 해결
{: #troubleshoot}

{{site.data.keyword.block_storage_is_short}}를 작성하거나 관리할 때 문제가 발생할 수 있습니다. 보통은 일부 손쉬운 단계를 수행하여 복구할 수 있습니다. 문제, 증상, 가능한 원인 및 해결 방법은 다음 절에 설명되어 있습니다.
{:shortdesc}

## 지정된 지역의 볼륨을 검색할 수 없음
{: #troubleshoot-topic-1}

하나 이상의 블록 스토리지 볼륨에 대한 정보를 해당 지역에 대해 검색할 수 없습니다.
{: tsSymptoms}

다음과 같은 원인이 적용될 수 있습니다.

* 볼륨 이름과 정보가 UI 또는 CLI 출력에서 누락되었습니다.
* 사용자 지역 이외의 지역에서 볼륨에 액세스하려고 시도했을 수 있습니다.
* 2세대 볼륨에 액세스하려고 시도했을 수 있습니다.
{: tsCauses}

볼륨이 가상 서버 인스턴스에서 분리되어 삭제되지 않았는지 확인하십시오. 모든 가상 서버 인스턴스의 목록에서 마지막으로 볼륨이 연결된 인스턴스를 검색하십시오.

1. [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 컴퓨팅 > 가상 서버 인스턴스**로 이동하십시오.

1. 모든 가상 서버의 목록에서 가상 서버 인스턴스를 선택하십시오.

볼륨이 예상대로 연결되지 않았으며 볼륨 목록에 나타나지 않는 경우에는 삭제되었을 가능성이 있습니다.  볼륨을 삭제하면 해당 데이터가 완전히 제거되므로 이를 복원할 수 없습니다.  

CLI를 사용하는 경우에는 볼륨을 보기 위해 올바른 구문을 입력했는지 확인하십시오. [CLI에서 모든 블록 스토리지 볼륨 보기](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)를 참조하십시오. 올바른 리소스 그룹 또는 구역을 지정했는지 확인하십시오.
{: tsResolve}

## 이름 또는 ID로 볼륨을 삭제할 수 없음
{: #troubleshoot-topic-2}

이름 또는 ID로 블록 스토리지 볼륨을 삭제할 수 없습니다.
{: tsSymptoms}

볼륨 이름 및 ID가 허용되지 않습니다.
{: tsCauses}

볼륨 이름 또는 ID가 올바르며 볼륨이 가상 서버 인스턴스에 연결되지 않았는지 확인하십시오. 또한 볼륨이 보류 상태가 아닌지도 확인하십시오.
{: tsResolve}
