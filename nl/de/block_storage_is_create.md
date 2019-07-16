---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Blockspeicherdatenträger in der {{site.data.keyword.cloud_notm}}-Konsole erstellen
{: #creating-block-storage}
[comment]: # (verknüpfter Hilfeabschnitt)

Sie können einen Blockspeicherdatenträger beim Erstellen einer virtuellen Serverinstanz erstellen oder einen eigenständigen Datenträger erstellen, der zu einem späteren Zeitpunkt zu einer Instanz zugeordnet wird.
{:shortdesc}

Stellen Sie zunächst sicher, dass ein [{{site.data.keyword.vpc_short}} erstellt](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started) wurde.
{:important}

## Blockspeicherdatenträger beim Erstellen einer neuen Instanz erstellen und zuordnen
{: #create-from-vsi}

1. Erstellen Sie eine Instanz. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Datenverarbeitung > Virtuelle Serverinstanzen für VPC > Neue Instanz**.
1. [Konfigurieren Sie die virtuelle Serverinstanz](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers). Wählen Sie unter **Zugeordnete Blockspeicherdatenträger** den Eintrag **Neuer Blockspeicherdatenträger** aus.
1. Geben Sie die in der folgenden Tabelle beschriebenen Informationen ein. Klicken Sie danach auf **Datenträger erstellen**.

| Feld | Wert |
|-------|-------|
| Name  | Geben Sie einen aussagefähigen Namen für Ihren Datenträger an, z. B. einen Namen, der die Funktion des Datenträgers in Bezug auf Datenverarbeitung oder Workload beschreibt. Sie können eine Kombination aus alphanumerischen Zeichen und Ziffern eingeben und den Namen später gegebenenfalls bearbeiten. |
| Profil | Wählen Sie [Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) aus und wählen Sie in der Liste mit den E/A-Operationen pro Sekunde (IOPS) die Leistungsstufe aus, die Sie benötigen. Wenn Ihre Leistungsanforderungen keiner vordefinierten IOPS-Tier entsprechen, wählen Sie [Benutzerdefiniert](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) aus und danach einen IOPS-Wert in dem Bereich für die jeweilige Datenträgergröße aus. Klicken Sie auf den Link für **Speichergröße**, um eine Tabelle mit Größen und IOPS-Bereichen anzuzeigen. |
| Automatisch löschen | Aktivieren Sie diese Funktion, wenn der Datenträger automatisch gelöscht werden soll, sobald die zugeordnete virtuelle Serverinstanz gelöscht wird. Sie können diese Einstellung später auf der Seite mit den Details des virtuellen Servers ändern. |
| IOPS | Wählen Sie 3, 5 oder 10 IOPS/GB für ein Profil mit IOPS-Leistungsstufen aus. |
| Größe | Geben Sie einen GB-Wert für die Datenträgergröße ein. Datenträgergrößen können zwischen 10 GB und 2 TB liegen. |
| Verschlüsselung | Die Verschlüsselung mit von IBM verwalteten Schlüsseln ist auf allen Datenträgern standardmäßig aktiviert. Sie können auch **Benutzerverwaltet** auswählen und Ihren eigenen Verschlüsselungsschlüssel verwenden. Informationen zu den Voraussetzungen sowie eine Anleitung zum Einrichten einer benutzerverwalteten Verschlüsselung finden Sie unter [Blockspeicherdatenträger mit benutzerverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Tabelle 1. Angabe von Blockspeicherdatenträgerwerten bei der Bereitstellung einer Instanz" caption-side="top"}

Es wird ein Blockspeicherdatenträger erstellt und der virtuellen Serverinstanz zugeordnet. Nach Abschluss des Vorgangs wird die Liste **Zugeordnete Blockspeicherdatenträger** auf der Seite mit den Instanzdetails mit dem neuen Datenträger aktualisiert.

Ein Blockspeicherdatenträger kann jeweils nur einem einzigen virtuellen Server zugeordnet sein. Auf der Übersichtsseite für Blockspeicherdatenträger können Sie Details zu der virtuellen Serverinstanz anzeigen, indem Sie den Namen der Instanz unter **Zugeordnete Instanzen** auswählen.

## Eigenständigen Blockspeicherdatenträger erstellen
{: #create-standalone-vol}

Sie können einen Blockspeicherdatenträger unabhängig von der Bereitstellung eines virtuellen Servers erstellen und den Datenträger zu einem späteren Zeitpunkt einer Instanz zuordnen.

1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicherdatenträger für VPC** und wählen Sie **Neuer Datenträger** aus.
1. Geben Sie die in der folgenden Tabelle beschriebenen Informationen ein, um den neuen Blockspeicherdatenträger zu definieren.
1. Klicken Sie danach auf **Datenträger erstellen**. Sie kehren daraufhin zu der Seite 'Blockspeicherdatenträger' zurück, in der eine Nachricht darauf hinweist, dass der Datenträger erstellt wird. Eine weitere Nachricht wird angezeigt, wenn das Erstellen des Datenträgers abgeschlossen ist.
1. Details des neuen Datenträgers können Sie anzeigen, indem Sie den Link **Ressource anzeigen** in der zweiten Nachricht auswählen, um zur Seite mit den Datenträgerdetails zu navigieren.

| Feld | Wert |
|-------|-------|
| Name  | Geben Sie einen aussagefähigen Namen für den Datenträger an. Geben Sie z. B. einen Namen an, der die Funktion des Datenträgers in Bezug auf Datenverarbeitung oder Workload beschreibt. Sie können bis zu 40 alphanumerische Zeichen eingeben und den Namen später bei Bedarf bearbeiten. |
| Ressourcengruppe | Geben Sie eine Ressourcengruppe an. Ressourcengruppen erleichtern die Verwaltung von Kontoressourcen für Zugriffssteuerungs- und Abrechnungszwecke. Informationen zum Einrichten einer Ressourcengruppe finden Sie im Abschnitt mit bewährten [Verfahren für das Zusammenfassen von Ressourcen in Ressourcengruppen](/docs/resources?topic=resources-bp_resourcegroups#setuprgs).|
| Tags | Geben Sie einen Tag an, um Ihre Ressourcen zu strukturieren. Bei einem Tag handelt es sich um eine Bezeichnung, die Sie einer Ressource zuordnen, um das Filtern von Ressourcen in Ihrer Ressourcenliste zu vereinfachen. Weitere Informationen zu Tags finden Sie unter [Mit Tags arbeiten](/docs/resources?topic=resources-tag). |
| Standort | Die Verfügbarkeitszone in Ihrer Region, die von VPC übernommen wurde (z. B. US South 1). |
| Größe | Geben Sie einen GB-Wert für die Datenträgergröße ein. Datenträgergrößen können zwischen 10 GB und 2 TB liegen. |
| IOPS | Wählen Sie [IOPS-Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) aus und wählen Sie die Kachel mit der gewünschten Leistungsstufe aus. |
| Angepasst | Wählen Sie je nach Größe des angegebenen Datenträgers einen IOPS-Wert im Bereich für die Datenträgergröße aus. Klicken Sie auf den Link für **Speichergröße**, um eine Tabelle mit Größen und IOPS-Bereichen anzuzeigen. Weitere Informationen finden Sie unter [Angepasstes IOPS-Profil](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). |
| Verschlüsselung | Die Verschlüsselung mit von IBM verwalteten Schlüsseln ist auf allen Datenträgern standardmäßig aktiviert. Wählen Sie die Option für eine benutzerverwaltete Verschlüsselung aus, wenn eigene Verschlüsselungsschlüssel verwendet werden sollen. Informationen hierzu finden Sie unter [Blockspeicherdatenträger mit benutzerverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Tabelle 2. Werte für das Definieren eines Blockspeicherdatenträgers" caption-side="top"}

Möchten Sie Blockspeicherdatenträger lieber über die Befehlszeilenschnittstelle erstellen? Informationen hierzu finden Sie unter [Blockspeicherdatenträger über die Befehlszeilenschnittstelle erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).
{: tip}

## Weitere Schritte
{: #next-step-creating-block-storage}

Wenn Sie die Seite 'Blockspeicherdatenträger' aktualisieren, wird der neue Datenträger am Anfang der Liste der Datenträger angezeigt. Wenn der Datenträger erfolgreich erstellt wurde, wird der Status 'Verfügbar' angezeigt. Bei eigenständigen Datenträgern ist die Spalte für den Zuordnungstyp leer (-). Das Aktionsmenü (...) am Ende einer Tabellenzeile enthält einen Link für das [Zuordnen eines Blockspeicherdatenträgers zu einer Instanz](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Sie können weitere Blockspeicherdatenträger erstellen oder vorhandene Datenträger verwalten.

* [Details zu einem Blockspeicherdatenträger anzeigen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Zuordnung eines Datenträgers zu einer virtuellen Serverinstanz aufheben](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [Blockspeicherdatenträger löschen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
