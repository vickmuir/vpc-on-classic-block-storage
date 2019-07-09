---

copyright:
  years: 2019
lastupdated: "2019-06-17"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

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

# CLI를 사용하여 블록 스토리지 볼륨 보기
{: #viewing-block-storage-cli}

CLI에서 블록 스토리지 볼륨에 대한 세부사항이나 모든 볼륨에 대한 요약 정보를 봅니다. 

## 시작하기 전에
{: #before-viewing-block-storage-cli}

다음의 CLI 플러그인을 다운로드, 설치 및 초기화했는지 확인하십시오. 

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} 지역 API CLI

자세한 정보는 [VPC용 {{site.data.keyword.cloud_notm}} CLI 참조서](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)의 전제조건을 참조하십시오.

## CLI를 사용하여 블록 스토리지 볼륨에 대한 세부사항 보기
{: #viewvol-cli}

볼륨에 대한 세부사항을 표시하려면 다음 명령을 지정하십시오. 

```bash
ibmcloud is volume VOLUME_ID [--json]
```

예: 

이 예에서는 볼륨 ID를 사용하여 볼륨 세부사항을 표시합니다. 

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

볼륨이 가상 서버 인스턴스에 연결된 경우에는 볼륨 연결 및 인스턴스의 이름과 ID도 표시됩니다. 

## CLI를 사용하여 모든 블록 스토리지 볼륨 보기
{: #viewall-vol-cli}

이 명령을 실행하여 모든 볼륨에 대한 요약 정보를 나열할 수 있습니다. 

```bash
ibmcloud is volumes [--json]
```

예: 

다음 예에서는 가용성 구역의 모든 리소스 그룹에 대한 모든 볼륨을 표시합니다.  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

리소스 그룹 ID 또는 이름을 지정하면 리소스 그룹에 속하는 볼륨으로 목록이 필터링됩니다. 이 매개변수를 생략하면 모든 리소스 그룹으로 기본값이 설정됩니다. 특정 가용성 구역의 모든 볼륨을 볼 수도 있습니다. 

기본적으로 페이지당 처음 25개의 볼륨이 표시됩니다. 

## CLI를 사용하여 볼륨 연결에 대한 세부사항 보기
{: #viewvol-attachment-cli}

가상 서버 인스턴스에 대한 볼륨 연결의 세부사항을 보려면 다음 명령을 실행하십시오.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

인스턴스 ID와 볼륨 연결 ID를 지정하십시오. 선택사항으로, JSON 형식으로 세부사항을 내보낼 수 있습니다. 

## CLI를 사용하여 모든 볼륨 연결에 대한 세부사항 보기

가상 서버 인스턴스에 대한 모든 볼륨 연결을 보려면 다음 명령을 실행하십시오.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## CLI를 사용하여 볼륨 프로파일 보기
{: #viewvol-profiles-cli}

사용자 지역에서 사용 가능한 모든 볼륨 프로파일을 나열하려면 다음 명령을 실행하십시오.

```bash
ibmcloud is volume-profiles [--json]
```

예: 

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## CLI를 사용하여 특정 볼륨 프로파일 보기
{: #viewvol-profile-cli}

사용자 지역의 특정 볼륨 프로파일을 보려면 다음 명령을 실행하십시오.

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME 값은 10iops-tier, 5iops-tier, general-purpose 및 custom입니다. 

예: 

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

{{site.data.keyword.cloud}} 콘솔을 사용한 블록 스토리지 볼륨 보기를 원하십니까? 자세한 정보는 [블록 스토리지 볼륨 보기](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)를 참조하십시오.
{: tip}

## 다음 단계
{: #next-step-viewing-block-storage-cli}

추가 볼륨을 작성하거나 기존 블록 스토리지 볼륨을 관리하십시오. 

* [블록 스토리지 볼륨 작성(CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [블록 스토리지 볼륨 관리(CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
