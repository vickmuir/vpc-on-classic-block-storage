---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# CLI를 사용하여 블록 스토리지 볼륨 관리
{: #managing-block-storage-cli}

명령행 인터페이스(CLI)에서 {{site.data.keyword.block_storage_is_short}}를 관리하십시오. 볼륨 이름을 업데이트하거나 볼륨 첨부 파일을 업데이트하거나 볼륨을 분리하거나 볼륨을 삭제하십시오.
{:shortdesc}

## 시작하기 전에
{: #before-managing-block-storage-cli}

1. 다음의 CLI 플러그인을 다운로드, 설치 및 초기화했는지 확인하십시오.
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 플러그인

   자세한 정보는 [VPC용 {{site.data.keyword.cloud_notm}} CLI 참조](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)의 내용을 참조하십시오.
   
   vpc 인프라 플러그인을 처음 설치할 때 대상 세대를 1 세대로 설정해야 합니다(`ibmcloud is target --gen 1`).
   {:important}
   
2. 이미 [{{site.data.keyword.vpc_short}}를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)했는지 확인하십시오.

## 볼륨 이름 업데이트
{: #update-vol-name}

볼륨 이름을 변경하려면 볼륨 이름 또는 ID를 지정한 후 새 이름을 명시하십시오.

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

예:

```bash
$ ibmcloud is volume-update 933c8781-f7f5-4a8f-8a2d-3bfc711788ee --name demo-volume-update
Updating volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount 01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo-volume-update
Capacity                                100
IOPS                                    1000
Profile                                 5iops-tier
Encryption                              -
Encryption                              provider managed
Status                                  available
Created                                 2019-05-20 10:09:28
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Zone                                    us-south-2
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Volume Attachment Instance Reference    none
```
{: screen}

## CLI를 사용하여 볼륨 연결 업데이트
{: #update-vol-name-cli}

`instance-volume-attachment-update` 명령을 사용하여 기본 자동 삭제 설정을 변경하고 볼륨 연결 이름을 업데이트할 수 있습니다.

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

`--name` 매개변수를 사용하고 볼륨 연결에 대한 새 이름을 지정하십시오.

연결된 인스턴스를 삭제할 때 볼륨을 자동으로 삭제하려면 `--auto-delete true`를 지정하십시오.

`볼륨 연결 인스턴스 참조`의 세부사항을 표시하는 예:

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## CLI를 사용하여 볼륨 분리
{: #detach-vol-attachment-cli}

`instance-volume-attachment-detach` 명령을 사용하여 인스턴스에서 볼륨을 분리하고 볼륨 연결을 삭제할 수 있습니다. 블록 스토리지 볼륨은 삭제되지 않습니다. 나중에 [이를 다른 인스턴스에 연결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli)할 수 있습니다.

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## CLI를 사용하여 블록 스토리지 볼륨 삭제
{: #delete-vol-cli}

`volume-delete` 명령을 사용하고 블록 스토리지 볼륨 삭제를 위한 볼륨 ID를 지정하십시오.

**참고:** 활성 블록 스토리지 볼륨은 삭제할 수 없습니다. 우선 [가상 서버에서 이를 분리](#detach-vol-attachment-cli)해야 합니다.

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

예:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

{{site.data.keyword.cloud}} 콘솔을 사용한 블록 스토리지 볼륨 관리를 원하십니까? 자세한 정보는 [블록 스토리지 볼륨 관리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)를 참조하십시오.
{:tip}

## 다음 단계
{: #next-step-managing-block-storage-cli}

[CLI를 사용하여 추가 볼륨을 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)하십시오.

기존 블록 스토리지 볼륨에 문제가 있으면 문제점을 직접 해결하고 처리할 수 있습니다. 자세한 정보는 [블록 스토리지의 문제점 해결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot)을 참조하십시오.
