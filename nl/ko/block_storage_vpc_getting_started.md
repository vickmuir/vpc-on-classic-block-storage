---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, getting started, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

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
{:shortdesc: .shortdesc}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# {{site.data.keyword.block_storage_is_short}} 시작하기
{: #getting-started}

이 튜토리얼은 Virtual Private Cloud(VPC)에서 {{site.data.keyword.block_storage_is_short}} 볼륨 작성을 시작하는 데 도움이 됩니다.
{: .shortdesc}

## 시작하기 전에
{: #block-storage-before-you-begin}

시작하려면 우선 구현에 도움이 될 수 있는 컨텐츠를 검토하십시오. {{site.data.keyword.cloud}} 및 {{site.data.keyword.block_storage_is_short}}가 처음이십니가? 다음 정보가 도움이 될 수 있습니다.

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [VPC용 블록 스토리지 정보](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

{{site.data.keyword.cloud_notm}} 계정에 등록하십시오. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 등록](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}을 참조하십시오.

## 1단계 - 스토리지 요구사항 결정
{: #determine-storage-requirements}

적절한 스토리지 요구사항의 범용 워크로드를 실행 중이십니까? 아니면 사용자의 워크로드가 고용량과 고성능을 요구하는 I/O 집약 워크로드입니까? 용량과 성능을 결정하는 방법에 대해 자세히 알아보려면 [블록 스토리지 용량 및 성능](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance)을 참조하십시오. 또한 [프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles)을 참조하여 스토리지 요구사항을 가장 잘 충족할 수 있는 IOPS 프로파일 옵션을 알아보십시오. 

가상 서버 인스턴스도 작성 중이십니까? [가상 서버 프로파일을 스토리지 프로파일과 연관시키는 방법](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage)을 참조하십시오.

## 2단계 - 블록 스토리지의 크기 지정 및 가격
{: #size-price-block-storage}

블록 스토리지 볼륨에 대한 [IOPS 티어 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)을 선택하십시오.  선택사항으로, 사전 정의된 IOPS 티어 내에 속하지 않는 잘 정의된 성능 요구사항이 있는 경우에는 [사용자 정의 IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)을 선택하십시오. 

블록 스토리지 볼륨의 크기와 성능을 선택한 후에 [가격](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing) 정보를 참조하면 볼륨 가격을 책정하고 비용 청구 방법을 파악하는 데 도움이 됩니다.

## 3단계 - {{site.data.keyword.cloud_notm}} 계정에 로그인
{: block-storage-log-into-ibm-account}

[{{site.data.keyword.cloud_notm}} 카탈로그](https://{DomainName}/catalog){: external}에서 {{site.data.keyword.block_storage_is_short}} 주문 양식에 액세스하십시오. IBM ID와 비밀번호를 사용하십시오.

## 4단계(선택사항) - {{site.data.keyword.vpc_short}}에 대한 액세스 확인

Virtual Private Cloud(VPC) 내에서 볼륨을 작성하려면 우선 [VPC를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console)해야 합니다. VPC 외부에서 독립형 볼륨을 작성하려면 이 단계를 건너뛰십시오. 나중에 {{site.data.keyword.vpc_short}}에 대한 액세스를 요청하여 인스턴스에 액세스하고 별도로 작성한 블록 스토리지 볼륨을 연결할 수 있습니다. {{site.data.keyword.vpc_short}}에 대한 자세한 정보는 [VPC 시작하기 튜토리얼](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)을 참조하십시오.

## 5단계 - 블록 스토리지 볼륨 작성

[{{site.data.keyword.cloud_notm}} 콘솔(UI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)에서 또는 [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)나 [{{site.data.keyword.vpc_short}} API](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}를 사용하여 볼륨 작성을 시작하십시오. IBM Cloud Developer 도구를 사용한 IBM Cloud CLI 설치에 대한 자세한 정보는 [IBM Cloud Developer 도구 시작하기](/docs/cli?topic=cloud-cli-getting-started)를 참조하십시오.

## 다음 단계
{: #next-step-block-storage-getting-started}

블록 스토리지를 작성한 후에는 다음의 추가 옵션을 탐색하십시오.

* [볼륨에 대한 세부사항 보기](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [블록 스토리지 볼륨 관리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
