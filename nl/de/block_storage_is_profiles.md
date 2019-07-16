---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}


# Profile
{: #block-storage-profiles}

Wenn Sie sekundäre {{site.data.keyword.block_storage_is_short}}-Datenträger über die {{site.data.keyword.cloud_notm}}-Konsole, -Befehlszeilenschnittstelle oder -API bereitstellen, geben Sie ein IOPS-Profil an, das am besten für Ihre Speicheranforderungen geeignet ist. Die Profile stehen in Form von drei vordefinierten IOPS-Tier-Profilen und einem angepassten IOPS-Profil zur Verfügung. IOPS-Tiers bieten eine garantierte IOPS/GB-Leistung für Datenträger mit bis zu 2 TB an Kapazität. Sie können auch ein angepasstes IOPS-Profil angeben und Datenträgerkapazität und E/A-Operationen pro Sekunde in einem Bereich definieren.

## Profile mit IOPS-Tiers
{: #tiers}

Beim Blockspeicher stehen drei vordefinierte IOPS-Tiers zur Auswahl, mit denen Sie eine optimale Leistung für Ihre Datenverarbeitungsworkloads vorgeben und Engpässe vermeiden können. Sie können Datenträger wie in der folgenden Tabelle beschrieben in Ihrer Verfügbarkeitszone mit garantierten IOPS-Werten bereitstellen:

| IOPS-Tier | Workload | Datenträgergröße | Max. IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | Allgemeine Workloads - Workloads, bei denen kleine Datenbanken für Webanwendungen gehostet oder VM-Plattenimages für einen Hypervisor gespeichert werden | 10 GB bis 1 TB | Bis zu 3.000 IOPS |
| | | Über 1 TB bis 2 TB | 3 IOPS/GB bis zu 6.000 IOPS |
| 5 IOPS/GB | Workloads mit hoher Ein-/Ausgabeintensität - Workloads, die sich durch einen hohen Prozentsatz aktiver Daten auszeichnen, z. B. transaktions- und andere leistungsorientierte Datenbanken | 10 GB bis 600 GB | Bis zu 3.000 IOPS |
| | | Über 600 GB bis 2 TB | 5 IOPS/GB bis zu 10.000 IOPS|
| 10 IOPS/GB | Anspruchsvolle Speicherworkloads - datenintensive Workloads, die von NoSQL-Datenbanken erstellt werden, Datenverarbeitung für Video, maschinelles Lernen und Analysen | 10 GB bis 300 GB | Bis zu 3.000 IOPS |
| | | Über 300 GB bis 2 TB | 10 IOPS/GB bis zu 20.000 IOPS |
{: caption="Tabelle 1. IOPS-Tiers und Leistung" caption-side="top"}

Der maximale Durchsatz für alle für Blockspeicher verfügbaren IOPS-Tiers beträgt ausgerichtet an einer Blockgröße von 16 KB 750 MB/s.

## Angepasstes IOPS-Profil
{: #custom}

Angepasste IOPS-Werte sind hilfreich, wenn Ihre Leistungsanforderungen genau definiert sind und keinem vordefinierten IOPS-Tier entsprechen. Sie können die IOPS-Werte anpassen, indem Sie die Gesamt-IOPS für den Datenträger in dem Bereich für die zugehörige Datengröße angeben. Sie können Datenträger mit 100 bis 20.000 IOPS bereitstellen.

Die folgende Tabelle enthält die verfügbaren IOPS-Bereiche für die verschiedenen Datenträgergrößen.

| Datenträgergröße (GB) | IOPS-Bereich |
|-------------|--------------|
| 10 - 39   | 100 - 1.000 |
| 40 - 79 | 100 - 2.000 |
| 80 - 99 | 100 - 4.000 |
| 100 - 499 | 100 - 6.000 |
| 500 - 999 | 100 - 10.000 |
| 1.000 - 1.999 | 100 - 20.000 |
{: caption="Tabelle 2. Verfügbare IOPS-Werte entsprechend der Datenträgergröße" caption-side="top"}

## Zusammenhang zwischen Profilen virtueller Server und Speicherprofilen
{: #vsi-profiles-relate-to-storage}

Bei Profilen für virtuelle Server handelt es sich um eine Kombination von vCPU und RAM, die umgehend zum Starten einer virtuellen Serverinstanz instanziiert werden kann. Sie können ein Profil aus einer von [drei Profilfamilien](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles),
auswählen, das für Ihre Workloadanforderungen geeignet ist. Die Anforderungen können sich von allgemeinen Workloads bis hin zu CPU- und speicherintensive Workloads erstrecken.  

Speicherprofile (IOPS-Tiers wie angepasste Speicherprofile) stellen ebenso einen Kapazitäts- und Leistungsbereich für sekundäre Datenträger bereit. Standardmäßig wird beim Erstellen
einer virtuellen Serverinstanz ein primärer Bootdatenträger mit 100 GB erstellt. Sie können auch sekundäre Datenträger erstellen und zuordnen.  
Wenn Sie bei der Instanzerstellung einen sekundären Datenträger erstellen, wählen Sie ein Speicherprofil aus, das dem Speicherbedarf für Ihre Datenverarbeitungsworkloads
am besten entspricht. Im Allgemeinen wachsen mit zunehmendem Speicherbedarf für Datenverarbeitungsworkloads auch die Anforderungen an die IOPS-Leistung. Die folgende Tabelle verdeutlicht diesen Zusammenhang.

| IOPS-Tier-Speicherprofil | Profil des virtuellen Servers |
|-----------------|------------------------|
| 3 IOPS/GB       | [Ausgewogen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) für allgemeine Workloads |
| 5 IOPS/GB       | [Datenverarbeitung](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) für intensive CPU-Anforderungen |
| 10 IOPS/GB      | [Hauptspeicher](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) für speicherintensive Workloads |

## IOPS-Profile anzeigen
{: #view-iops-profiles}

Sie können verfügbare IOPS-Profile über die {{site.data.keyword.cloud_notm}}-Konsole, -Befehlszeilenschnittstelle oder -API anzeigen.

### IBM Cloud-Konsole verwenden
{: using-console-iops-profile}

 Wenn Sie [einen Blockspeicherdatenträger über die {{site.data.keyword.cloud_notm}}-Konsole erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), wählen Sie **Tiers** im Dropdown-Menü aus.

 Stattdessen können Sie auch **Benutzerdefiniert** und dann einen IOPS-Wert im Bereich für die jeweilige Datenträgergröße auswählen. Klicken Sie auf den Link für Speichergröße, um eine Tabelle mit Größen und IOPS-Bereichen anzuzeigen.

 ### Befehlszeilenschnittstelle verwenden
 {: using-cli-iops-profiles}

 Führen Sie den folgenden Befehl aus, um die Liste der verfügbaren Profile mit Hilfe der Befehlszeilenschnittstelle anzuzeigen:
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### API verwenden
{: using-api-iops-profiles}

Mit der folgenden cURL-API-Anforderung werden alle Datenträgerprofile abgerufen.

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## Zugehörige Informationen

Informationen zu den Profilen "Ausgewogen", "Datenverarbeitung" und "Hauptspeicher" für {{site.data.keyword.vsi_is_short}} finden Sie unter [Profile](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).
