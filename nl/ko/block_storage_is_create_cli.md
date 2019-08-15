---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM CLoud, VPC, virtual private cloud, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# CLI를 사용하여 블록 스토리지 볼륨 작성
{: #creating-block-storage-cli}

명령행 인터페이스(CLI)를 사용하여 {{site.data.keyword.block_storage_is_short}} 볼륨을 작성할 수 있습니다.
{:shortdesc}

## 시작하기 전에
{: #before-creating-block-storage-cli}

1. 다음의 CLI 플러그인을 다운로드, 설치 및 초기화했는지 확인하십시오.
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 플러그인

   자세한 정보는 [VPC용 {{site.data.keyword.cloud_notm}} CLI 참조](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)의 내용을 참조하십시오.
   
   vpc 인프라 플러그인을 처음 설치할 때 대상 세대를 1 세대로 설정해야 합니다(`ibmcloud is target --gen 1`).
   {:important}
   
2. 이미 [{{site.data.keyword.vpc_short}}를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)했는지 확인하십시오.

## CLI를 사용하여 블록 스토리지 볼륨 작성
{: #create-vol-cli}

다음 명령을 실행하십시오.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

예:

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

용량(MB로 표기됨)은 10 - 2,000GB 범위일 수 있습니다.  IOPS 값은 볼륨 크기에 따라 1,000 - 20,000 IOPS 범위일 수 있습니다. IOPS 값을 지정하지 않으면 기본적으로 볼륨 프로파일당 유효한 구성으로 설정됩니다. 자세한 정보는 [볼륨 크기를 기반으로 한 IOPS 범위](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)의 표를 참조하십시오.

위의 예에 있는 볼륨 ID는 가상 서버 인스턴스에 블록 스토리지 연결, 블록 스토리지 볼륨 세부사항 보기 및 볼륨 삭제 시에 사용됩니다.

{{site.data.keyword.cloud}} 콘솔에서 블록 스토리지 볼륨 작성을 원하십니까? 자세한 정보는 [블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)을 참조하십시오.
{: tip}

## 다음 단계
{: #next-step-creating-block-storage-cli}

[블록 스토리지 볼륨 연결(CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)을 수행하십시오.
