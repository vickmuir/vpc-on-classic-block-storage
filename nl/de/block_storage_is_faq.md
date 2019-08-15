---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# Häufig gestellte Fragen zu {{site.data.keyword.block_storage_is_short}}
{: #block-storage-vpc-faq}

Auf dieser Seite finden Sie häufig gestellte Fragen zu {{site.data.keyword.block_storage_is_short}}. Dieses Topic enthält Antworten zu zahlreichen Fragen in Bezug auf die Erstellung und Verwaltung von Blockspeicherdatenträgern. Wenn Sie weitere Fragen haben, die hier beantwortet werden sollen, senden Sie uns Ihr Feedback über den Link **Probleme** oder den Link **Topic bearbeiten**.
{:shortdesc}

## Wie kann ich Speicher für meine Instanzen zuordnen?
{: faq}

Beim Erstellen einer virtuellen Serverinstanz können Sie einen [Blockspeicherdatenträger erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi), der der Instanz zugeordnet werden soll.  Sie können auch [eigenständige Datenträger erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol) und diese Datenträger Ihren Instanzen zu einem späteren Zeitpunkt zuordnen.

## Wie viele Instanzen können einen bereitgestellten Blockspeicherdatenträger gemeinsam nutzen?
{: faq}

Ein Blockspeicherdatenträger kann jeweils nur einer einzigen Serverinstanz zugeordnet sein. Eine gemeinsame Nutzung eines Datenträgers durch mehrere Instanzen ist nicht möglich.

## Wie viele sekundäre Blockspeicherdatenträger (für Daten) können einer Instanz zugeordnet werden?
{: faq}

Instanzen mit weniger als 4 vCPUs können bis zu 4 sekundäre Blockspeicherdatenträger zuordnen.

Instanzen mit mindestens 4 vCPUs können bis zu 12 sekundäre Blockspeicherdatenträger zuordnen.

## Werden bei der Bereitstellung von E/A-Operationen pro Sekunde die zugeordneten IOPS-Werte pro Instanz oder pro Datenträger umgesetzt?
{: faq}

Die E/A-Operationen pro Sekunde werden auf Datenträgerebene umgesetzt.

## Wie werden die E/A-Operationen pro Sekunde gemessen?
{: faq}

IOPS-Werte werden anhand eines Belastungsprofils mit 16-KB-Blöcken und 50 % wahlfreien Leseoperationen und 50 % wahlfreien Schreiboperationen gemessen. Workloads, die von diesem Profil abweichen, erreichen möglicherweise eine schlechte Leistung.

## Was sind IOPS-Profile?
{: faq}

IOPS-Profile definieren die IOPS/GB-Leistung für Datenträger mit verschiedenen Kapazitäten. Es stehen drei vordefinierte [IOPS-Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) zur Auswahl, die eine garantierte IOPS-Leistung für die Erfüllung Ihrer Workloadanforderungen bieten. Sie können auch [angepasste IOPS-Werte](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) definieren und einen IOPS-Bereich für eine von Ihnen ausgewählte Datenträgergröße angeben. Angepasste IOPS-Werte sind hilfreich, wenn Ihre Leistungsanforderungen genau definiert sind und keinem vordefinierten IOPS-Tier entsprechen.

## Was sind die maximalen IOPS-Werte, die ich für meine Datenträger erwarten kann?
{: faq}

Die maximalen E/A-Operationen pro Sekunde für sekundäre Datenträger variieren je nach Datenträgergröße und dem ausgewählten IOPS-Tier-Profil. Der maximale IOPS-Wert für einen für allgemeine Zwecke eingesetzten Datenträger mit bis zu 1 TB beträgt beispielsweise 3.000 E/A-Operationen pro Sekunde. Weitere Informationen finden Sie unter [Profile mit IOPS-Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). Definieren Sie bei Verwendung eines [angepassten IOPS-Profils](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) auch einen Mindest- und Höchstbereich für die jeweilige Datenträgergröße.

## Was geschieht, wenn ich beim Messen der Leistung eine kleinere Blockgröße verwende?
{: faq}

Bei Verwendung kleinerer Blockgrößen kann der Höchstwert für E/A-Operationen pro Sekunde weiterhin erreicht werden, der Durchsatz reduziert sich jedoch. Ein Datenträger mit 6000 E/A-Operationen pro Sekunde hat bei verschiedenen Blockgrößen beispielsweise den folgenden Durchsatz:

* 16 KB * 6000 E/A-Operationen pro Sekunde = ~93,75 MB/sec
* 8 KB * 6000 E/A-Operationen pro Sekunde = ~46,88 MB/Sek.
* 4 KB * 6000 E/A-Operationen pro Sekunde = ~23,44 MB/Sek.

## Welche Nutzungsgebühren fallen an und gibt es Größenbeschränkungen?
{: faq}

Weitere Informationen zur Abrechnung finden Sie unter [Preisgestaltung bei Block Storage for VPC](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing). Es gelten bestimmte Grenzen.
Weitere Informationen zu Größenbeschränkungen und Begrenzungen für Ihre Instanz von {{site.data.keyword.cloud}} Virtual Private Cloud und mit der Instanz verfügbaren Ressourcen finden Sie unter [Größenbeschränkungen](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas).

## Kann ich nach dem Erstellen eines Datenträgers die zugehörige Kapazität zu einem späteren Zeitpunkt erhöhen?
{: faq}

Nein, die Kapazität eines Datenträgers kann nicht nachträglich erhöht werden. Erstellen Sie vor dem Bereitstellen eines Blockspeicherdatenträgers eine Kapazitätsschätzung, die Raum für zukünftiges Wachstum lässt. Beziehen Sie auch die Anzahl der benötigten Datenträger und die Kapazität dieser Datenträger in die Überlegungen ein. [Datenträgeranzahl und Kapazitätsgrenzwerte verwalten](/docs/vpc-on-classic?topic=vpc-on-classic-managingstoragelimits) enthält weitere Informationen hierzu. 

## Ist vor dem ersten Zugriff ein Initialisieren des Datenträgers erforderlich, damit der erwartete Durchsatz erzielt wird?
{: faq}

Eine Initialisierung des Datenträgers ist nicht erforderlich. Der angegebene Durchsatz wird sofort bei Bereitstellung des Datenträgers erreicht.

## Kann ich verschlüsselte Datenträger erstellen?
{: faq}

Alle Blockspeicherdatenträger werden durch eine von IBM verwaltete Verschlüsselung (Standardeinstellung) oder über den Key Protect-Service mit Ihren eigenen Verschlüsselungsschlüsseln verschlüsselt. Informationen hierzu finden Sie unter [Blockspeicherdatenträger mit benutzerverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

## Woran kann ich erkennen, welchen Verschlüsselungstyp ein Datenträger aufweist?
{: faq}

Wenn Sie in der Benutzerschnittstelle die Liste sämtlicher Blockspeicherdatenträger anzeigen, enthält die Verschlüsselungsspalte einen Eintrag für die vom Provider verwaltete Verschlüsselung oder die benutzerverwaltete Verschlüsselung.

Geben Sie Folgendes ein, um die Eigenschaften eines Datenträgers über die Befehlszeilenschnittstelle anzuzeigen:

```bash
ibmcloud is volume (DATENTRÄGERNAME | DATENTRÄGER-ID)
```

## Wie sicher sind meine Daten?
{: faq}

Bei allen Blockspeicherdatenträger werden ruhende Daten über eine von IBM verwaltete Verschlüsselung oder Ihre eigenen Verschlüsselungsschlüssel verschlüsselt. Von IBM verwaltete Schlüssel werden generiert, sicher in einer von Consul unterstützten Blockspeichervault gespeichert und anschließend vom System verwaltet. Benutzerverwaltete Schlüssel werden mit dem IBM Key Protect-Service sicher verwaltet.

## Was mache ich mit Datensicherungen für die Wiederherstellung nach einem Disaster-Recovery?
{: faq}

Block Storage for VPC sichert Ihre Daten in zonenredundant in Ihrer Region. Darüber hinaus sollten Sie für eine zusätzliche Sicherung Ihrer Daten sorgen. Ziehen Sie auch eine Verwendung von [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started) in Betracht, das Disaster-Recoveryfunktionen wie das Klonen und Replizieren von Datenträgern und das Erstellen von Datenträgersnapshots beinhaltet.

## Wie viele Datenträger können bereitgestellt werden?
{: faq}

Sie können bis zu 1.000 Blockspeicherdatenträger pro Region bereitstellen.

## Welche Strategie sollte ich bei der Datenträgerverwaltung verfolgen?
{: faq}

Ermitteln Sie die Kapazität, die Sie im Hinblick auf das erwartete Wachstum benötigen. Die Datenträgergröße kann nach der Bereitstellung nicht erweitert werden. Sie können jedoch bei Bedarf neue Datenträger erstellen. Wenn Ihre Leistungsanforderungen genau definiert sind, bietet sich möglicherweise auch das Auswählen der Option [Angepasste IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) an, die einen bestimmten IOPS-Bereich für bestimmte Datenträgergrößen bereitstellt.

## Wie wird der Bootdatenträger für eine virtuelle Serverinstanz erstellt und welcher Zusammenhang besteht zwischen Bootdatenträger und Imagedatei?
{: faq}

Die Bootplatte, auch Bootdatenträger genannt, wird erstellt, wenn Sie eine virtuelle Serverinstanz bereitstellen. Bei dem Bootdatenträger einer Instanz handelt es sich um ein geklontes Image des Images der virtuellen Maschine. Der Bootdatenträger wird gelöscht, wenn Sie die Instanz löschen, der der Datenträger zugeordnet ist.

## Beeinträchtigen Firewalls und Sicherheitsgruppen die Leistung?
{: faq}

Es hat sich bewährt, speicherbezogenen Datenverkehr in einem VLAN auszuführen, das die Firewall umgeht. Eine Ausführung des Speicherdatenverkehrs über Software-Firewalls erhöht die Latenz und beeinträchtigt die Speicherleistung.

## Wann kann ich einen Blockspeicherdatenträger für Daten löschen?
{: faq}

Sie können einen Blockspeicherdatenträger für Daten nur löschen, wenn der Datenträger keiner virtuellen Serverinstanz zugeordnet ist. [Heben Sie die Zuordnung des Datenträgers auf](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach), bevor Sie die Löschanforderung für den Datenträger ausgeben. Bootdatenträger werden freigegeben und gelöscht, wenn die zugehörige Instanz gelöscht wird.

## Was passiert mit meinen Daten, wenn ich einen sekundären Blockspeicherdatenträger lösche?
{: faq}

Wenn Sie einen Blockspeicherdatenträger mit Daten löschen, werden alle Verweise auf die Daten auf diesem Datenträger entfernt und die Daten sind nicht mehr zugänglich. Wenn Sie den physischen Speicher später erneut für ein anderes Konto bereitstellen, wird eine neue Gruppe von Verweisen zugeordnet. Es gibt keine Möglichkeit, mit dem neuen Konto auf Daten zuzugreifen, die zuvor auf der physischen Speichereinheit gespeichert waren. Die gesamte neue Gruppe von Verweisen weist Nullwerte auf. Werden neue Daten auf den Datenträger geschrieben, werden die nicht mehr zugänglichen Daten überschrieben.

## Mit welcher Latenz beim Leistungsverhalten muss ich bei meinem Blockspeicher rechnen?
{: faq}

Die Ziellatenz im Speicher beträgt weniger als 1 Millisekunde. Da der vorliegende Blockspeicher mit Datenverarbeitungsinstanzen in einem gemeinsamen Netz verbunden ist, hängt die genaue Leistungslatenz vom Netzverkehr während eines bestimmten Zeitraums ab.

## Kann ich gemeinsam genutzten Speicher in einem Cluster mit mehreren Zonen einrichten?
{: faq}

In IBM Cloud sind die Speicheroptionen in einer Verfügbarkeitszone lokalisiert. Es empfiehlt sich nicht, gemeinsam genutzten Speicher über mehrere Zonen hinweg zu verwalten.

Verwenden Sie stattdessen eine klassische Serviceoption für IBM Cloud-Daten wie {{site.data.keyword.cos_full}} oder {{site.data.keyword.cloudantfull}}, wenn Ihre Daten über mehrere Zonen und Regionen hinweg gemeinsam genutzt werden müssen.

## Ich verfüge über Datenträger in der klassischen Infrastruktur. Kann ich diese Datenträger in VPC portieren?
{: faq}

Nein. VPC bietet Zugang zu neuen Verfügbarkeitszonen in MZR (Multi-Zone Regions). Datenverarbeitungs-, Netz- und Speicherressourcen sind speziell für VPC konzipiert.
