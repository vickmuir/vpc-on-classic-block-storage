---

Copyright:
  years: 2019
lastupdated: "2019-07-23"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance, customer-managed encryption

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 고객 관리 암호화로 블록 스토리지 볼륨 작성
{: #block-storage-encryption}

기본적으로 {{site.data.keyword.block_storage_is_short}} 부트 및 데이터 볼륨은 IBM 관리 암호화로 암호화됩니다. 고객 루트 키 작성 또는 가져오기를 위해 지원되는 키 관리 서비스를 사용하여 고객 관리 암호화된 볼륨을 작성할 수도 있습니다. 고객 관리 암호화는 인스턴스 프로비저닝 중에 작성된 부트 및 데이터 볼륨에 대한 옵션입니다.  독립형 데이터 볼륨을 작성할 때 고객 관리 암호화를 지정할 수도 있습니다.
{:shortdesc}

## 블록 스토리지 볼륨의 키 관리 서비스
{: #key-mgt-services-for-storage}

{{site.data.keyword.keymanagementserviceshort}} 및 {{site.data.keyword.hscrypto}}(특정 [지역](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)에서 사용 가능함) 등 2개의 키 관리 서비스를 사용할 수 있습니다. {{site.data.keyword.cloud_notm}} 데이터 센터는 키 보호를 위해 전용 하드웨어 보안 모듈(HSM)을 제공합니다. 다음 표는 각 서비스에 대한 정보를 제공합니다.

| 키 관리 서비스 | HSM 암호화 인증 |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 *레벨 2* 준수 |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 *레벨 4* 준수 |
{: caption="표 1. {{site.data.keyword.block_storage_is_short}}의 키 관리 서비스" caption-side="top"}

## 전제조건
{: #custom-managed-vol-prereqs}

고객 관리 암호화로 블록 스토리지 볼륨을 작성하려면 우선 키 관리 서비스를 프로비저닝하고 고객 루트 키를 작성하거나 가져와야 합니다.
또한 클라우드 블록 스토리지와 키 관리 서비스 간의 액세스 권한도 부여해야 합니다. 이러한 전제조건이 완료되면 고객 관리 암호화를 사용하는 블록 스토리지 볼륨의 작성을 시작할 수 있습니다.

다음 단계는 {{site.data.keyword.keymanagementserviceshort}}에 특정하지만 일반적인 플로우는 {{site.data.keyword.hscrypto}}에도 적용됩니다.  {{site.data.keyword.hscrypto}}를 사용 중이면 [{{site.data.keyword.hscrypto}} 정보](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)에서 해당 지시사항을 참조하십시오.
{:note}

1. [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) 서비스를 프로비저닝하십시오.

   새 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스를 프로비저닝하면 블록 스토리지 볼륨의 고객 관리 암호화에 필요한 최신 업데이트가 포함되도록 보장합니다. 2019년에 작성된 {{site.data.keyword.keymanagementserviceshort}} 인스턴스에는 고객 관리 암호화 지원에 필요한 확장기능이 포함되어 있습니다.
   {: tip}

2. {{site.data.keyword.keymanagementservicelong_notm}}에서 고객 루트 키(CRK)를 [작성](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)하거나 [가져오십시오](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys).
3. IBM {{site.data.keyword.iamshort}}(IAM)에서 **Cloud Block Storage**(소스 서비스)와 **{{site.data.keyword.keymanagementserviceshort}}**(대상 서비스) 간의 [액세스 권한을 부여](/docs/iam?topic=iam-serviceauth#serviceauth)하십시오.

## UI를 사용하여 고객 관리 암호화 데이터 볼륨 작성
{: #data-vol-encryption-ui}

독립형 볼륨으로 또는 인스턴스 프로비저닝 중에 새 블록 스토리지 볼륨을 작성할 때 고객 관리 암호화를 지정할 수 있습니다.

가상 서버 인스턴스 작성 시에 암호화된 볼륨을 작성하려면 [고객 관리 암호화로 가상 서버 인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok)을 참조하십시오.

독립형 볼륨 작성 시에 고객 관리 암호화를 지정하려면 다음 단계를 수행하십시오.

1. {{site.data.keyword.cloud_notm}} 콘솔에서 **메뉴 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg) > VPC 인프라 > 스토리지 > 블록 스토리지 볼륨**으로 이동하십시오.
모든 블록 스토리지 볼륨의 목록이 표시됩니다.
1. **새 볼륨**을 선택하십시오.
1. **새 블록 스토리지 볼륨** 페이지에서 **암호화** 섹션의 필드를 업데이트하십시오. 자세한 정보는 다음 표를 참조하십시오. 변경이 완료되면 **볼륨 작성**을 클릭하십시오.

| 필드 |값 |
| ----- | ----- |
| 암호화 | _제공자 관리_가 기본 암호화 모드입니다. 고객 관리 암호화를 사용하려면 키 관리 서비스({{site.data.keyword.keymanagementserviceshort}} 또는 {{site.data.keyword.hscrypto}})를 선택하십시오. 키 관리 서비스 인스턴스에는 고객 관리 암호화에 사용할 고객 루트 키가 포함되어야 합니다. |
| 암호화 서비스 인스턴스 |계정에 다수의 키 관리 서비스 인스턴스가 프로비저닝되어 있으면 고객 관리 암호화에 사용할 고객 루트 키가 포함된 인스턴스를 선택하십시오. |
| 키 이름 |볼륨 암호화에 사용할 {{site.data.keyword.keymanagementserviceshort}} 인스턴스 내의 데이터 암호화 키를 선택하십시오. |
| 키 ID | 선택한 데이터 암호화 키와 연관된 키 ID를 표시합니다. |
{: caption="표 1. 고객 관리 암호화의 값" caption-side="top"}

## CLI를 사용하여 고객 관리 암호화 데이터 볼륨 작성
{: #data-vol-encryption-cli}

CLI를 사용하여 고객 관리 암호화로 블록 스토리지 볼륨을 작성하려면 `ibmcloud is volume-create` 명령에 `--encryption-key` 매개변수를 지정하십시오.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

`--encryption-key` 매개변수는 루트 키의 CRN을 취합니다. 키 관리 서비스 인스턴스에서 루트 키의 CRN을 가져오십시오. 자세한 정보는 [고객 관리 암호화의 가상 서버 인스턴스 문서](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)를 참조하십시오. CLI를 사용한 블록 스토리지 볼륨 작성에 대한 정보는 [CLI를 사용하여 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)을 참조하십시오.

다음의 예는 고객 관리 암호화로 작성된 새 볼륨을 보여줍니다.

```bash
$ ibmcloud is volume-create demo_volume custom us-south-1 --iops 1000 --encryption-key abccorp-kp-vpc-2 5437644a-c4b1-447f-9646-b1a2a4df61382
Creating volume demovolume in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          crn:v1:bluemix:public:kms:us-south:a/8d65fb1cf5e99e86dd7229ddef9e5b7b:b1abf7c5-381d-4f34-836e-5db7193250bc:key:fd57250e-908c-4785-a8a5-1f53176bcd2f
Encryption                              customer_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

인스턴스 프로비저닝 중에 고객 관리 암호화로 볼륨을 작성할 수도 있습니다.  자세한 정보는 [CLI를 사용하여 고객 관리 암호화로 인스턴스 및 볼륨 프로비저닝](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli)을 참조하십시오. 

## UI를 사용하여 고객 관리 암호화를 사용하도록 부트 볼륨 편집

UI에서 인스턴스 작성 시에 부트 볼륨 특성을 편집하여 고객 관리 암호화를 지정할 수 있습니다. 자세한 정보는 [고객 관리 암호화를 사용하는 볼륨으로 가상 서버 인스턴스 프로비저닝](docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-ui)을 참조하십시오.
