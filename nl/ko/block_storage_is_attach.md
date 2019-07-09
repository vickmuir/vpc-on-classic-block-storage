---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, block storage volume, volume, volume attachment, virtual server instance, instance

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

# UI를 사용하여 블록 스토리지 볼륨 연결
{: #attaching-block-storage}

UI에서 가상 서버 인스턴스의 블록 스토리지 볼륨을 작성하면 해당 볼륨이 기본적으로 인스턴스에 연결됩니다. 볼륨을 분리하면 이는 나중에 재연결이 가능한 연결되지 않은 볼륨으로 존재합니다. 이러한 사용 가능한 볼륨은 [모든 블록 스토리지 볼륨](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols)의 목록에 표시됩니다. 특정 인스턴스에 대한 세부사항을 볼 때나 모든 블록 스토리지 볼륨의 목록에서 다른 인스턴스에 볼륨을 연결할 수 있습니다.
{:shortdesc}

## 볼륨 연결 한계
{: #vol-attach-limits}

한 번에 하나의 블록 스토리지 볼륨만 가상 서버 인스턴스에 연결할 수 있지만, 다음의 한도로 다수의 서로 다른 블록 스토리지 볼륨을 하나의 인스턴스에 연결할 수 있습니다. 

* 4개 미만의 가상 CPU가 있는 인스턴스는 최대 4개의 블록 스토리지 2차 볼륨과 부트 볼륨에 연결될 수 있습니다.
* 4개 이상의 가상 CPU가 있는 인스턴스는 최대 12개의 블록 스토리지 2차 볼륨과 부트 볼륨에 연결될 수 있습니다.

## 가상 서버 인스턴스에 블록 스토리지 볼륨 연결
{: #attach}

모든 블록 스토리지 볼륨의 목록에서 다음 단계를 수행하십시오. 

1. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 스토리지 > VPC용 블록 스토리지 볼륨**으로 이동하십시오.
1. 볼륨 목록에서, 사용 가능한 연결되지 않은 볼륨에 대한 행의 끝에 있는 생략 기호(…)를 클릭하십시오. 컨텍스트 특정 조치 메뉴가 표시됩니다.
1. **인스턴스에 연결**을 선택하십시오. 
1. 사용 가능한 리소스의 목록에서 컴퓨팅 리소스(가상 서버 인스턴스)를 선택한 후 **연결**을 클릭하십시오.
1. 볼륨을 이미지에 연결 중임을 알리는 메시지가 볼륨 세부사항 페이지에 표시됩니다. 완료되면 이미지 이름이 **연결된 인스턴스** 아래에 나타납니다.

가상 서버 인스턴스 세부사항 페이지에서 블록 스토리지 볼륨을 연결할 수도 있습니다.

1. Virtual Private Cloud(VPC)의 [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}/vpc){: external}에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > 컴퓨팅 > VPC용 가상 서버 인스턴스**로 이동하십시오.
1. 모든 가상 서버 인스턴스의 목록에서 인스턴스를 선택하십시오. 연결된 블록 스토리지 볼륨이 있으면 이는 **연결된 블록 스토리지 볼륨** 아래에 나열됩니다.
1. **볼륨 연결**을 선택하십시오. 
1. 사용 가능한 리소스의 목록에서 볼륨을 선택하고 **연결**을 클릭하십시오. 볼륨을 연결 중임을 알리는 메시지가 인스턴스 세부사항 페이지에 표시됩니다. 완료되면 **연결된 블록 스토리지 볼륨** 목록이 새 볼륨을 포함하도록 업데이트됩니다.

CLI를 사용하여 블록 스토리지 볼륨을 수동으로 연결할 수도 있습니다. 자세한 정보는 [블록 스토리지 볼륨 연결(CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)을 참조하십시오.
{: tip}

## 다음 단계
{: #next-step-attaching-block-storage}

추가 볼륨을 작성하고 기존 볼륨을 관리하십시오. 다음 정보를 참조하십시오. 

* [IBM Cloud 콘솔에서 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [UI를 사용하여 블록 스토리지 볼륨 관리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
