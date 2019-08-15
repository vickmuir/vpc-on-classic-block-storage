---

copyright:
  years: 2019
lastupdated: "2019-07-22"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS, HPCS, Key Protect

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# {{site.data.keyword.block_storage_is_short}} 정보
{: #block-storage-about}
[comment]: # (링크된 도움말 항목)

{{site.data.keyword.block_storage_is_full}}(VPC)에서는 {{site.data.keyword.vpc_full}}(VPC) 내에서 프로비저닝할 수 있는 가상 서버 인스턴스(인스턴스)에 대한 하이퍼바이저 마운트된 고성능 데이터 스토리지를 제공합니다. VPC 인프라는 여러 지역과 영역 간의 신속한 스케일링 및 추가적인 성능과 보안을 제공합니다. {{site.data.keyword.vpc_short}}에 대한 자세한 정보는 [Virtual Private Cloud(VPC) 정보](/docs/vpc-on-classic?topic=vpc-on-classic-about)를 참조하십시오.
{:shortdesc}

{{site.data.keyword.block_storage_is_short}}는 1차  부트 볼륨과 2차 데이터 볼륨을 제공합니다. 부트 볼륨은 인스턴스 프로비저닝 중에 자동으로 작성되어 연결됩니다. 데이터 볼륨도 인스턴스 프로비저닝 중에 작성되어 연결될 수 있습니다. 또는 나중에 인스턴스에 연결할 수 있는 독립형 볼륨으로 작성될 수 있습니다. 데이터 보호를 위해 사용자 고유의 암호화 키를 사용하거나 IBM 관리 암호화를 선택할 수 있습니다. [IOPS 티어 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)을 사용하면 볼륨의 사전 정의된 성능 레벨을 지정할 수 있습니다. 또는 [사용자 정의 IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)을 선택하고 볼륨 용량과 IOPS 레벨을 정의할 수도 있습니다.

## VPC 볼륨의 블록 스토리지
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}}는 부트 볼륨이나 데이터 볼륨으로 인스턴스에 연결될 수 있는 블록 레벨 데이터 스토리지 볼륨을 제공합니다. 지역당 최대 750개의 블록 스토리지 볼륨을 구성할 수 있습니다. 추가 용량을 위해 단일 인스턴스에 다수의 블록 스토리지 데이터 볼륨을 연결할 수 있습니다. 인스턴스에 연결할 수 있는 볼륨의 수는 인스턴스에 포함된 vCPU의 수에 따라 결정됩니다. 자세한 정보는 [볼륨 연결 한계](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits)를 참조하십시오.

### 부트 볼륨
{: #block-storage-vpc-boot-volumes}

인스턴스를 작성하면 100GB 부트 볼륨이 자동으로 작성되어 인스턴스에 연결됩니다. 부트 볼륨의 최대 IOPS는 3,000 IOPS입니다. [사용자 고유의 암호화 키](#about-customer-managed-encrytion)를 사용하여 부트 볼륨을 암호화하거나 기본 [제공자 관리 암호화](#about-provider-managed-encryption)를 사용할 수 있습니다. 부트 볼륨은 수동으로 분리와 삭제가 불가능하지만 인스턴스를 삭제하면 삭제됩니다.

### 2차 데이터 볼륨
{: #secondary-data-volumes}

블록 스토리지 데이터 볼륨은 총 용량 범위가 10GB - 2000GB인 2차 볼륨입니다. 데이터 볼륨의 최대 IOPS는 선택한 IOPS 티어 프로파일과 볼륨 크기에 따라 다릅니다. 예를 들어, 최대 1TB의 범용 볼륨에 대한 최대 IOPS는 3,000 IOPS입니다. 자세한 정보는 [티어 IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)을 참조하십시오.

사용자는 인스턴스 프로비저닝 시에 또는 독립형 볼륨으로 데이터 볼륨을 작성합니다. 볼륨을 인스턴스에 연결할 때까지 독립형 볼륨은 연결되지 않은 상태로 존재합니다. 인스턴스 프로비저닝의 일부로서 데이터 볼륨을 작성하면 볼륨이 자동으로 인스턴스에 연결됩니다.  

블록 스토리지 데이터 볼륨은 [특정 한계](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits) 내에서 사용자 지역 내의 사용 가능한 인스턴스에 연결될 수 있습니다. 이러한 볼륨은 인스턴스가 삭제될 때 기본적으로 분리됩니다. 기본적으로 분리됨으로써 사용자 데이터는 가상 서버 인스턴스 라이프사이클 이후에도 지속될 수 있습니다. 이는 인스턴스와의 볼륨 연관만 제거합니다. 분리된 후에는 데이터 볼륨을 수동으로 삭제할 수 있습니다. 또는 볼륨 작성 시에 인스턴스가 삭제될 때 이를 [자동으로 분리하고 삭제](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete)하도록 지정할 수 있습니다.

데이터 볼륨은 기본적으로 IBM 관리 암호화로 암호화됩니다. 선택사항으로, [사용자 고유의 암호화 키](#about-customer-managed-encrytion)를 사용하여 데이터 볼륨을 암호화할 수 있습니다.

## 저장 데이터(data-at-rest)에 대한 Block Storage 암호화
{: #encryption}

{{site.data.keyword.cloud_notm}}에서는 보안 요구사항을 진중히 받아들이며 안전 유지를 위한 데이터 암호화 가능성의 중요성을 잘 알고 있습니다. 독립형 볼륨을 작성하거나 인스턴스 작성의 일부로서 볼륨을 작성하는 경우에는 IBM 제공자 관리 암호화를 사용한 데이터 보호나 사용자 고유의 암호화 키 사용을 선택할 수 있습니다.  

### 제공자 관리 암호화
{: #about-provider-managed-encryption}

기본적으로 모든 부트 및 데이터 볼륨은 IBM 제공자 관리 암호화로 암호화됩니다. 이 서비스에 대한 추가 비용은 없습니다. 또는 성능에 영향을 주지도 않습니다. 제공자 관리 암호화는 다음의 산업 표준 프로토콜을 사용합니다.

* AES-256 암호화
* 키는 KMIP(Key Management Interoperability Protocol)를 사용하여 내부에서 관리됩니다.
* 스토리지는 FIPS(Federal Information Processing Standard) 문서 140-2, FISMA(Federal Information Security Management Act), HIPAA(Health Insurance Portability and Accountability Act)에 대해 검증을 받습니다. 스토리지는 PCI(Payment Card Industry), Basel II, California Security Breach Information Act(SB 1386) 및 EU Data Protection Directive 95/46/EC 준수에 대해서도 검증을 받습니다.

### 고객 관리 암호화
{: #about-customer-managed-encrytion}

사용자 고유의 암호화 키를 사용하여 블록 스토리지 볼륨을 암호화할 수 있습니다. 데이터 볼륨의 경우에는 볼륨 작성 시에 고객 관리 암호화를 지정합니다. 부트 볼륨의 경우에는 인스턴스 작성 중에 부트 볼륨 특성을 편집하고 고객 관리 암호화를 지정할 수 있습니다. 프로시저에 대해서는 [고객 관리 암호화로 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)을 참조하십시오.

고객 관리 암호화를 사용하면 암호화 키가 키 관리 서비스({{site.data.keyword.keymanagementservicelong_notm}} 또는 {{site.data.keyword.hscrypto}})에 업로드됩니다. VPC 인프라는 사전 구성된 키 관리 서비스 인스턴스의 키를 찾은 후에 볼륨을 암호화합니다. 전제조건 및 일회성 설정 프로시저는 [고객 관리 암호화로 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)을 참조하십시오.

가상 서버 인스턴스 프로비저닝 중에 볼륨에 대한 고객 관리 암호화 작성에 대한 자세한 정보는 [블록 스토리지의 고객 관리 암호화](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys)를 참조하십시오.

## 관련 정보

VPC에서 인스턴스 생성 및 관리에 대한 자세한 정보는 [VPC용 가상 서버 정보](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud)를 참조하십시오.

VPC용 블록 스토리지 작성을 시작하려면 [블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage)을 참조하십시오.

{{site.data.keyword.block_storage_is_short}}는 VPC에 대한 고유 기능을 제공하며 이는 클래식 인프라 스토리지와 호환 가능하지 않습니다. 클래식 인프라의 {{site.data.keyword.blockstoragefull}}에 관심이 있으면 [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About)를 참조하십시오.
{:note}
