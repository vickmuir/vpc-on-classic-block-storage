---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# VPC용 블록 스토리지에 대한 자주 묻는 질문(FAQ)
{: #block-storage-vpc-faq}

## 내 인스턴스의 스토리지를 어떻게 할당합니까? 
{: faq}

가상 서버 인스턴스를 작성할 때 해당 인스턴스에 연결될 [블록 스토리지 볼륨을 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi)할 수 있습니다. 또는 [독립형 볼륨을 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol)하고 나중에 이를 인스턴스에 연결할 수도 있습니다. 

## 프로비저닝된 블록 스토리지 볼륨을 공유할 수 있는 인스턴스 수는 몇 개입니까?
{: faq}

블록 스토리지 볼륨은 한 번에 하나의 인스턴스에만 연결될 수 있습니다. 인스턴스는 동일한 볼륨을 공유할 수 없습니다.

## 인스턴스에 연결될 수 있는 블록 스토리지 2차(데이터) 볼륨의 수는 몇 개입니까?
{: faq}

4개 미만의 vCPU가 있는 인스턴스는 최대 4개의 블록 스토리지 2차 볼륨에 연결될 수 있습니다.

4개 이상의 vCPU가 있는 인스턴스는 최대 12개의 블록 스토리지 2차 볼륨에 연결될 수 있습니다.

## IOPS를 프로비저닝하는 경우, 할당된 IOPS는 인스턴스로 적용됩니까 아니면 볼륨으로 적용됩니까?
{: faq}

IOPS는 볼륨 레벨에서 적용됩니다. 

## IOPS를 어떻게 측정합니까? 
{: faq}

IOPS는 랜덤 50% 읽기와 50% 쓰기로 16KB의 로드 프로파일을 기반으로 측정됩니다. 이 프로파일과는 다른 워크로드에서는 성능 저하가 발생할 수 있습니다. 

## IOPS 프로파일이란 무엇입니까? 
{: faq}

IOPS 프로파일은 다양한 용량의 볼륨에 대한 IOPS/GB 성능을 정의합니다. 워크로드 요구사항을 충족하기 위한 보장된 IOPS 성능을 제공하는 3개의 사전 정의된 [IOPS 티어](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) 중에서 선택할 수 있습니다. 또한 [사용자 정의 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)를 정의하고 선택한 볼륨 크기에 대한 IOPS 범위를 지정할 수도 있습니다. 사용자 정의 IOPS는 사전 정의된 IOPS 티어 내에 속하지 않는 잘 정의된 성능 요구사항이 있는 경우에 적합한 옵션입니다.

## 내 데이터 볼륨에 대해 기대할 수 있는 최대 IOPS는 얼마입니까?
{: faq}

데이터 볼륨의 최대 IOPS는 선택한 IOPS 티어 프로파일과 볼륨 크기에 따라 다릅니다. 예를 들어, 최대 1TB의 범용 볼륨에 대한 최대 IOPS는 3,000 IOPS입니다. 자세한 정보는 [티어 IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)을 참조하십시오. [사용자 정의 IOPS 프로파일](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)을 선택한 경우에는 제공된 볼륨 크기의 최소 및 최대 범위도 정의하십시오. 

## 성능을 측정할 때 더 작은 블록 크기를 사용하면 어떻게 됩니까?
{: faq}

더 작은 블록 크기를 사용해도 여전히 최대 IOPS를 얻을 수 있지만 처리량이 낮아집니다. 예를 들어, 6000 IOPS의 볼륨의 처리량은 다양한 블록 크기에서 다음과 같습니다. 

* 16KB * 6000 IOPS == ~93.75MB/sec
* 8KB * 6000 IOPS == ~46.88MB/sec
* 4KB * 6000 IOPS == ~23.44MB/sec

## 사용량에 따라 비용이 청구되며 할당량 한계가 있습니까?
{: faq}

비용 청구 방법에 대한 자세한 정보는 [VPC용 블록 스토리지의 가격](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing)을 참조하십시오. 특정 한계가 적용됩니다.
{{site.data.keyword.cloud}} Virtual Private Cloud(VPC)의 할당량과 한계 및 여기서 사용 가능한 리소스에 대한 자세한 정보는 [할당량](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas)을 참조하십시오.

## 볼륨 작성 이후 나중에 해당 용량을 늘릴 수 있습니까?
{: faq}

아니오, 볼륨의 용량은 늘릴 수 없습니다. 블록 스토리지 볼륨을 프로비저닝하기 전에 계획된 확장에 대비하여 충분한 용량을 추정하도록 권장합니다.

## 예상된 처리량을 얻으려면 볼륨의 사전 워밍이 필요합니까? 
{: faq}

볼륨의 사전 워밍은 필요하지 않습니다. 볼륨을 프로비저닝하는 즉시 지정된 처리량을 확인할 수 있습니다.

## 암호화된 볼륨을 작성할 수 있습니까? 
{: faq}

모든 블록 스토리지 볼륨은 사용자 고유의 암호화 키를 사용하여 Key Protect 서비스를 통해 또는 IBM 관리 암호화(기본값)로 암호화됩니다. 자세한 정보는 [고객 관리 암호화로 블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)을 참조하십시오. 

## 볼륨에 있는 암호화의 유형을 어떻게 알 수 있습니까?
{: faq}

UI에서 모든 블록 스토리지 볼륨의 목록을 보면 암호화 열이 제공자 관리 또는 고객 관리 암호화를 표시합니다. 

CLI에서 볼륨의 특성을 표시하려면 다음을 입력하십시오. 

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## 내 데이터는 얼마나 안전합니까? 
{: faq}

모든 블록 스토리지 볼륨은 IBM 관리 암호화 또는 사용자 고유의 암호화 키를 사용하여 안전하게 암호화됩니다. IBM 관리 키는 생성된 후 Consul에서 지원하는 블록 스토리지 저장소에서 안전하게 저장되어 시스템에 의해 유지보수됩니다. 고객 관리 키는 IBM Key Protect 서비스를 사용하여 안전하게 관리됩니다.

## 재해 복구에 필요한 데이터 백업 관련 작업은 무엇입니까?
{: faq}

VPC용 블록 스토리지는 사용자 지역의 중복된 결함 구역 간의 데이터를 보호합니다. 데이터의 별도 백업도 함께 수행하도록 권장합니다. 볼륨 복제, 스냅샷 및 복제 등의 재해 복구 기능을 제공하는 [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started)의 사용을 고려할 수도 있습니다. 

## 프로비저닝 가능한 볼륨의 수는 몇 개입니까?
{: faq}

지역당 최대 1,000개의 블록 스토리지 볼륨을 프로비저닝할 수 있습니다. 

## 내 볼륨을 관리하려면 어떤 전략을 사용해야 합니까?
{: faq}

예상되는 확장에 따라 필요한 용량을 판별하십시오. 볼륨 크기는 프로비저닝 이후 확장이 불가능합니다. 그러나 필요하면 새 볼륨을 작성할 수 있습니다. 또한 잘 정의된 성능 요구사항이 있는 경우에는 볼륨 크기당 특정 범위의 IOPS를 제공하는 [사용자 정의 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom)의 선택을 고려할 수도 있습니다. 

## 가상 서버 인스턴스의 부트 디스크는 어떻게 작성되며 이는 이미지 파일과 어떻게 관련됩니까? 
{: faq}

부트 볼륨이라고도 하는 부트 디스크는 가상 서버 인스턴스를 프로비저닝할 때 작성됩니다. 인스턴스의 부트 디스크는 가상 머신 이미지의 복제된 이미지입니다. 연결된 인스턴스를 삭제하면 부트 볼륨이 삭제됩니다.

## 방화벽 또는 보안 그룹이 성능에 영향을 줍니까?
{: faq}

방화벽을 우회하는 VLAN에서 스토리지 트래픽을 실행하는 것이 가장 좋습니다. 소프트웨어 방화벽을 통해 스토리지 트래픽을 실행하면 대기 시간이 늘어나며 스토리지 성능에 부정적인 영향을 줍니다. 

## 언제 블록 스토리지 데이터 볼륨을 삭제할 수 있습니까? 
{: faq}

가상 서버 인스턴스에 연결되지 않았을 때만 블록 스토리지 데이터 볼륨을 삭제할 수 있습니다. 삭제하기 전에 [볼륨을 분리](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)하십시오. 부트 볼륨은 인스턴스 삭제 시에 분리되어 삭제됩니다. 

## 블록 스토리지 데이터 볼륨을 삭제하면 내 데이터는 어떻게 됩니까?
{: faq}

블록 스토리지 데이터 볼륨을 삭제하면 해당 볼륨의 데이터에 대한 모든 포인터가 제거되며 데이터에 전혀 액세스할 수 없게 됩니다. 나중에 다른 계정으로 물리적 스토리지를 다시 프로비저닝하면 새 포인터 세트가 지정됩니다. 이 새 계정이 물리적 스토리지에 있었던 데이터에 액세스할 수 있는 방법은 없습니다. 새 포인터 세트는 모두 0을 표시합니다. 새 데이터가 볼륨에 쓰여질 때 이는 이는 액세스 불가능한 데이터를 겹쳐씁니다. 

## 내 블록 스토리지에서 예상될 수 있는 성능 대기 시간은 얼마입니까?
{: faq}

스토리지 내의 목표 대기 시간은 1밀리초 미만입니다. 블록 스토리지가 공유 네트워크의 컴퓨팅 인스턴스에 연결되므로, 정확한 성능 대기 시간은 제공된 시간 범위 내의 네트워크 트래픽에 따라 다릅니다.

## 다중 구역 클러스터에서 공유 스토리지를 설정할 수 있습니까?
{: faq}

IBM Cloud에서는 스토리지 옵션이 가용성 구역으로 국한되어 있습니다. 다중 구역 간에 공유 스토리지를 관리하지 않도록 권장합니다. 

그 대신, 다중 구역과 지역 간의 데이터 공유가 필요하면 {{site.data.keyword.cos_full}} 또는 {{site.data.keyword.cloudantfull}} 등의 IBM Cloud 데이터 클래식 서비스 옵션을 사용하십시오. 

## 클래식 인프라에서 볼륨을 보유하고 있습니다. 이를 VPC에 이식할 수 있습니까? 
{: faq}

아니오. VPC는 다중 구역 지역의 새 가용성 구역에 대한 액세스를 제공합니다. 컴퓨팅, 네트워크 및 스토리지 리소스는 VPC에서 작동하도록 특별히 디자인되어 있습니다. 
