---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

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
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Blockspeicherkapazität und -leistung
{: #capacity-performance}

Die Auswahl der optimalen Blockspeicherdatenträgergröße und der Leistungsstufe für Ihre Workloads ist von Bedeutung. Wenn Sie Blockspeicher über die Benutzerschnittstelle oder die Befehlszeilenschnittstelle bereitstellen, können Sie die Größe Ihres Datenträgers und die Leistungsstufe auswählen.

### Kapazität
{: #block-storage-vpc-capacity}

Sie können 10 GB bis 2000 GB (2 TB) Kapazität pro sekundärem Blockspeicherdatenträger in Schritten von 1 GB angeben. Die Gesamtdatenträgerkapazität wird bestimmt, wenn Sie ein [IOPS-Profil](#iops-profiles) auswählen. Bootdatenträger weisen 100 GB auf.

### IOPS-Profile
{: #iops-profiles}

Wenn Sie {{site.data.keyword.block_storage_is_short}}-Datenträger bereitstellen, geben Sie ein [IOPS-Profil](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) an, das Ihre Speicheranforderungen am besten erfüllt. Die Profile stehen in Form von drei vordefinierten IOPS-Tier-Profilen und einem angepassten IOPS-Profil zur Verfügung. [IOPS-Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) stellen eine garantierte IOPS/GB-Leistung für Datenträger mit bis zu 2 TB an Kapazität bereit. Sie können auch ein [angepasstes IOPS-Profil](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) angeben und Datenträgerkapazität und E/A-Operationen pro Sekunde in einem Bereich definieren. Verwenden Sie zum Angeben eines Profils entweder die {{site.data.keyword.cloud_notm}}-Konsole, -Befehlszeilenschnittstelle oder -API.

## Auswirkung der Blockgröße auf die Leistung
{: #how-block-size-affects-performance}

Der IOPS-Wert basiert auf einer Blockgröße von 16 KB mit einer zu gleichen Teilen aus wahlfreien Lese- und Schreiboperationen bestehenden Workload. Ein 16-KB-Block entspricht einer Schreiboperation auf dem Datenträger. Der Basisdurchsatz wird durch den Umfang an E/A-Operationen pro Sekunde multipliziert mit der Blockgröße von 16 KB bestimmt. Je höher der von Ihnen angegebene IOPS-Wert ist, umso höher ist der Durchsatz. Der maximale Durchsatz für einen Blockspeicherdatenträger beträgt 750 MB/s.

Die für Ihre Anwendung gewählte Blockgröße beeinflusst die Speicherleistung unmittelbar. Liegt die Blockgröße unter 16 KB, wird der IOPS-Grenzwert vor dem Durchsatzgrenzwert erreicht. Liegt die Blockgröße über 16 KB, wird dagegen der Durchsatzgrenzwert vor dem IOPS-Grenzwert erreicht. Die folgende Tabelle enthält einige Beispiele, wie Blockgröße und IOPS-Werte den Durchsatz beeinflussen.

| Blockgröße (KB) | IOPS | Durchsatz (MB/s) |
|-----------------|------|-------------------|
| 4 (typisch für Linux) | 1.000 | 4 |
| 8 (typisch für Oracle) | 1.000  | 8 |
| 16 | 1.000 | 16 |
| 32 (typisch für SQL Server) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="In Tabelle 1 werden Beispiele für die Beeinflussung des Durchsatzes durch Blockgröße und IOPS-Rate aufgeführt.<br/Durchschnittliche Ein-/Ausgabegröße x E/A-Operationen pro Sekunde = Durchsatz in MB/s." caption-side="top"}>
