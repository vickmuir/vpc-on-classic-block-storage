---

copyright:
  years: 2019
lastupdated: "2019-06-14"

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

# Informationen zu Block Storage for VPC
{: #block-storage-about}
[comment]: # (verknüpfter Hilfeabschnitt)

{{site.data.keyword.block_storage_is_full}} (VPC) stellt einen hypervisorbasierten Hochleistungsdatenspeicher für Ihre virtuellen Serverinstanzen (Instanzen) bereit, die Sie in {{site.data.keyword.vpc_full}} (VPC) bereitstellen können. Die VPC-Infrastruktur ermöglicht eine schnelle Skalierung über mehrere Regionen und Zonen hinweg und bietet zusätzliche Leistung und Sicherheit. Weitere Informationen zu {{site.data.keyword.vpc_short}} finden Sie unter [Informationen zu Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about).{:shortdesc}

{{site.data.keyword.block_storage_is_short}} stellt primäre Bootdatenträger und sekundäre Datenträger für Daten bereit. Bootdatenträger werden bei der Instanzbereitstellung automatisch erstellt und zugeordnet. Sekundäre Datenträger können bei der Instanzbereitstellung erstellt und zugeordnet werden oder als eigenständige Datenträger erstellt werden, die Sie zu einem späteren Zeitpunkt zu einer Instanz zuordnen können. Zum Schutz Ihrer Daten können Sie Ihren eigenen Verschlüsselungsschlüssel oder die von IBM verwaltete Verschlüsselung verwenden.
Mit [IOPS-Tier-Profilen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) können Sie eine vordefinierte Leistungsstufe für Ihre Datenträger angeben. Sie können auch ein [angepasstes IOPS-Profil](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) auswählen und eine eigene Datenträgerkapazität und IOPS-Stufe definieren.

## Blockspeicher für VPC-Datenträger
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} bietet Speicherdatenträger auf Blockebene, die einer Instanz als Bootdatenträger (primärer Datenträger) oder Datenträger für Daten (sekundäre Datenträger) zugeordnet werden können. Pro Region können Sie bis zu 750 Blockspeicherdatenträger konfigurieren. Sie können einer einzelnen Instanz mehrere sekundäre Blockspeicherdatenträger zuordnen, um zusätzliche Kapazität bereitzustellen. Die Anzahl der Datenträger, die einer Instanz zugeordnet werden können, richtet sich nach der Anzahl der vCPUs der jeweiligen Instanz. Weitere Informationen hierzu finden Sie in [Grenzwerte beim Zuordnen von Datenträgern](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits).

### Bootdatenträger
{: #block-storage-vpc-boot-volumes}

Wenn Sie eine Instanz erstellen, wird automatisch ein 100-GB-Bootdatenträger erstellt und der Instanz zugeordnet. Der Bootdatenträger verfügt über einen maximalen IOPS-Wert von 3.000 E/A-Operationen pro Sekunde. Sie können den Bootdatenträger unter Verwendung von [eigenen Verschlüsselungsschlüsseln](#about-customer-managed-encrytion) verschlüsseln oder die Standardverschlüsselung mit [vom Provider verwalteter Verschlüsselung](#about-provider-managed-encryption) verwenden. Ein Bootdatenträger kann nicht manuell zugeordnet und gelöscht werden, er wird jedoch gelöscht, wenn Sie die zugehörige Instanz löschen.

### Sekundäre Datenträger (für Daten)
{: #secondary-data-volumes}

Blockspeicherdatenträger für Daten stellen sekundäre Datenträger mit einem Gesamtkapazitätsbereich von 10 GB bis 2000 GB dar. Die maximalen E/A-Operationen pro Sekunde für sekundäre Datenträger variieren je nach Datenträgergröße und dem ausgewählten IOPS-Tier-Profil. Der maximale IOPS-Wert für einen für allgemeine Zwecke eingesetzten Datenträger mit bis zu 1 TB beträgt beispielsweise 3.000 E/A-Operationen pro Sekunde. Weitere Informationen hierzu finden Sie unter [Profile mit IOPS-Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). 

Sekundäre Datenträger werden als eigenständige Datenträger oder beim Bereitstellen einer Instanz erstellt. Eigenständige Datenträger weisen einen nicht zugeordneten Status auf, bis Sie den Datenträger zu einer Instanz zuordnen. Wenn Sie einen sekundären Datenträger bei der Instanzbereitstellung erstellen, wird der Datenträger der Instanz automatisch zugeordnet.  

Sekundäre Blockspeicherdatenträger können einer beliebigen verfügbaren Instanz Ihrer Region unter Berücksichtigung [bestimmter Grenzwerte](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits) zugeordnet werden. Diese Datenträger werden standardmäßig freigegeben, wenn die zugehörige Instanz gelöscht wird. Wenn Sie die Zuordnung aufheben, können Ihre Daten standardmäßig über den Lebenszyklus der virtuellen Serverinstanz hinaus bestehen bleiben. Es wird lediglich die Zuordnung des Datenträgers zu der Instanz entfernt. Sie können sekundäre Datenträger manuell löschen, nachdem sie freigegeben wurden, oder Sie können beim Erstellen eines Datenträgers angeben, dass der Datenträger [automatisch freigegeben und gelöscht werden](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete) soll, wenn die zugehörige Instanz gelöscht wird.

Sekundäre Datenträger werden standardmäßig mit von IBM verwalteter Verschlüsselung verschlüsselt. Bei Bedarf können Sie sekundäre Datenträger auch mit Ihrem [eigenen Verschlüsselungsschlüssel](#about-customer-managed-encrytion) verschlüsseln.

## Verschlüsselung für ruhende Daten
{: #encryption}

Bei {{site.data.keyword.cloud_notm}} wird dem Bedürfnis nach Sicherheit und der Bedeutung von Verschlüsselungsfunktionalität für die Datensicherheit Rechnung getragen. Wenn Sie einen eigenständigen Datenträger erstellen oder einen Datenträger beim Erstellen einer Instanz erstellen, können Sie auswählen, ob Ihre Daten mit von IBM verwalteter Verschlüsselung (vom Provider verwalteter Verschlüsselung) oder über Ihre eigenen Verschlüsselungsschlüssel geschützt werden sollen.  

### Vom Provider verwaltete Verschlüsselung
{: #about-provider-managed-encryption}

Standardmäßig werden primäre und sekundäre Datenträger (Bootdatenträger und Datenträger für Daten) mit von IBM verwalteter Verschlüsselung verschlüsselt. Es fallen keine zusätzlichen Kosten für diesen Service an und die Leistung wird dadurch nicht beeinträchtigt. Bei vom Provider verwalteter Verschlüsselung werden die folgenden Standardprotokolle der Branche verwendet:

* Verschlüsselung AES-256 (AES = Advanced Encryption Standard)
* Schlüssel werden unternehmensintern mit dem Protokoll KMIP (Key Management Interoperability Protocol) verwaltet.
* Die Speicherung wird per Federal Information Processing Standard (FIPS) Publication 140-2 für Konformität mit Federal Information Security Management Act (FISMA), Health Insurance Portability and Accountability Act (HIPAA) validiert. Die Speicherung ist auch für Payment Card Industry (PCI), Basel II, California Security Breach Information Act (SB 1386) und EU Data Protection Directive 95/46/EC validiert.

### Benutzerverwaltete Verschlüsselung
{: #about-customer-managed-encrytion}

Sie können Blockspeicherdatenträger mit Ihren eigenen Verschlüsselungsschlüsseln verschlüsseln. Bei sekundären Datenträgern geben Sie beim Erstellen des Datenträgers die benutzerverwaltete Verschlüsselung an. Bei Bootdatenträgern können Sie die Eigenschaften des Bootdatenträgers bei der Instanzerstellung bearbeiten und die benutzerverwaltete Verschlüsselung angeben. Informationen zur Vorgehensweise finden Sie unter [Blockspeicherdatenträger mit benutzerverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Bei der benutzerverwalteten Verschlüsselung wird Ihr Verschlüsselungsschlüssel in einen Schlüsselverwaltungsservice hochgeladen ({{site.data.keyword.keymanagementservicelong_notm}} oder {{site.data.keyword.hscrypto}}). Die VPC-Infrastruktur lokalisiert den Schlüssel in der Instanz des Schlüsselmanagementservice, die Sie zuvor konfiguriert haben, und verschlüsselt den Datenträger anschließend. Informationen zu den Voraussetzungen sowie eine Anleitung zum einmaligen Einrichten finden Sie unter [Blockspeicherdatenträger mit benutzerverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Weitere Informationen zum Erstellen einer benutzerverwalteten Verschlüsselung für Datenträger bei der Bereitstellung von virtuellen Serverinstanzen finden Sie unter [Benutzerverwaltete Verschlüsselung für Blockspeicher](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys).

## Zugehörige Informationen

Weitere Informationen zum Erstellen und Verwalten von Instanzen in VPC finden Sie unter [Informationen zu virtuellen Servern für VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

Einstiegsinformationen zum Erstellen von Blockspeicher für VPC finden Sie unter [Blockspeicherdatenträger erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage).

{{site.data.keyword.block_storage_is_short}} stellt Features bereit, die VPC auszeichnen, und ist nicht mit Speicher der klassischen Infrastruktur kompatibel. Wenn Sie sich für {{site.data.keyword.blockstoragefull}} in der klassischen Infrastruktur interessieren, lesen Sie den Abschnitt [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).{:note}
