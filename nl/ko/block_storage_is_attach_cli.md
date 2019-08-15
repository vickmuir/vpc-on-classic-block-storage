---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, CLI, block storage volume, volume, volume attachment, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# CLI를 사용하여 블록 스토리지 볼륨 연결
{: #attaching-block-storage-cli}

볼륨 연결은 {{site.data.keyword.block_storage_is_short}} 볼륨을 가상 서버 인스턴스에 연결합니다. 각 인스턴스에 [많은 볼륨 연결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)이 있을 수 있지만, 단일 볼륨 연결은 하나의 볼륨을 하나의 인스턴스에 연결합니다.
{:shortdesc}

## 시작하기 전에
{: #before-attaching-block-storage-cli}

1. 다음의 CLI 플러그인을 다운로드, 설치 및 초기화했는지 확인하십시오.
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 플러그인

   자세한 정보는 [VPC용 {{site.data.keyword.cloud_notm}} CLI 참조](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)의 내용을 참조하십시오.
   
   vpc 인프라 플러그인을 처음 설치할 때 대상 세대를 1 세대로 설정해야 합니다(`ibmcloud is target --gen 1`).
   {:important}
   
2. 이미 [{{site.data.keyword.vpc_short}}를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)했는지 확인하십시오.

## CLI를 사용하여 블록 스토리지 볼륨 연결
{: #attach-block-storage-cli}

현재 리소스 그룹의 가상 서버 인스턴스에 볼륨을 연결하려면 다음 명령을 실행하십시오.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME`은 볼륨 연결을 위해 제공되는 이름이며, INSTANCE_ID는 VSI의 ID입니다.

`VOLUME_ID`는 연결 중인 볼륨을 지정합니다.

VSI 삭제 시에 볼륨이 자동으로 삭제되도록 하려면 `--auto-delete true`를 지정하십시오.

사용 가능한 가상 서버 인스턴스 목록을 보려면 `ibmcloud is instances` 명령을 실행하십시오.

예:

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.xxx.xx.xx    -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.xxx.xx.x     -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             192.xxx.xxx.xx   -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             192.xxx.xxx.xxx  -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## 가상 서버 인스턴스에 연결된 볼륨의 세부사항 표시
{: #show-details-attached-vol}

볼륨을 연결한 후에는 `instance-volume-attachment` 명령에 인스턴스 ID와 볼륨 연결 ID를 지정하여 세부사항을 표시할 수 있습니다.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## 서버 인스턴스의 모든 볼륨 연결 나열

`instance-volume-attachments` 명령을 사용하고 인스턴스 ID를 지정하여 인스턴스의 모든 볼륨 연결을 볼 수 있습니다.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

{{site.data.keyword.cloud}} 콘솔의 사용을 원하십니까? 콘솔에서 볼륨을 연결하는 방법에 대한 정보는 [블록 스토리지 볼륨 연결](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage)을 참조하십시오.
{:tip}

## 볼륨 연결 JSON 작성
{: #volume_attachment_json}

CLI를 사용하여 가상 서버 인스턴스를 프로비저닝하고 프로세스의 일부로서 블록 스토리지 볼륨을 작성하는 경우에는 볼륨 연결 JSON을 지정해야 합니다. 파일로서 또는 명령에서 지정된 볼륨 연결 JSON은 볼륨 매개변수를 정의합니다. [인스턴스를 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)하고 `--volume-attach` 매개변수를 지정하는 경우 볼륨 JSON을 지정합니다. 예: `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

사용자 정의 볼륨을 정의하는 볼륨 연결 JSON 파일의 예는 다음과 같습니다.

```
[
    {
        "name": "myvolume-attachment",
        "delete_volume_on_instance_delete": true,
        "volume": {
            "name": "myvolume",
            "capacity": 100,
            "iops": 1000,
            "profile": {
                "name": "custom"
            }
        }
    }
]
```
{: screen}

## 다음 단계
{: #next-step-attaching-block-storage-cli}

추가 볼륨을 작성하고 기존 볼륨을 관리하십시오.  다음 정보를 참조하십시오.

* [CLI를 사용하여 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [CLI를 사용하여 블록 스토리지 볼륨 관리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
