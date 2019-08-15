---

copyright:
  years: 2019
lastupdated: "2019-07-24"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Details zum Blockspeicherdatenträger anzeigen
{: #viewing-block-storage}

Sie können Details zu einem {{site.data.keyword.block_storage_is_short}}-Datenträger oder eine Zusammenfassung der Informationen zu allen Datenträgern anzeigen.
{:shortdesc}

## Informationen zu allen Blockspeicherdatenträgern anzeigen
{: #viewvols}

Navigieren Sie zur Liste der Blockspeicherdatenträger. Rufen Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud das **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicher** auf.

Blockspeicherdatenträger werden standardmäßig für alle Ressourcengruppen in Ihrer Region angezeigt.  Die Liste aller **Block Storage for VPC-Datenträter** enthält die folgenden Informationen. 

| Feld | Beschreibung |
|-------|-------------|
| Status | Status des Datenträgers, der als Standardfilter für alle Zeilen dient. Informationen zum Datenträgerstatus finden Sie unter [Statusangaben für Blockspeicherdatenträger](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status). |
| Name | Wenn Sie auf den Namen eines Datenträgers klicken, werden Details zu dem jeweiligen Datenträger angezeigt. |
| Ressourcengruppe | Ressourcengruppen werden bei der VPC-Einrichtung definiert. Ressourcengruppen erleichtern die Verwaltung von Kontoressourcen für Zugriffssteuerungs- und Abrechnungszwecke. Informationen hierzu finden Sie in [Bewährte Verfahren für das Zusammenfassen von Ressourcen in Ressourcengruppen](docs/resources?topic=resources-bp_resourcegroups). |
| Standort | Die Verfügbarkeitszone in Ihrer Region, die von VPC übernommen wurde (z. B. US South 1). |
| Größe | Die Größe des von Ihnen angegebenen Datenträgers in GB. |
| Max. IOPS | Die maximal verfügbaren E/A-Operationen pro Sekunde auf dem Datenträger, die durch den von Ihnen angegebenen Wert für das allgemeine IOPS-Tier oder das angepasste Tier definiert werden. |
| Zuordnungstyp | "Daten" für einen sekundären Datenträger, der einer Instanz zugeordnet ist, und "Boot" für einen als Bootdatenträger zugeordneten Datenträger. Dieses Feld bleibt für Datenträger, die nicht zugeordnet sind, leer. |
| Verschlüsselung | Vom Provider verwaltete Verschlüsselung oder [benutzerverwaltete](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption) Verschlüsselung. |
| Aktionen (...) | Klicken Sie auf die Auslassungspunkte, um ein Menü mit kontextspezifischen Aktionen anzuzeigen, die Sie ausführen können.  Für einen verfügbaren, nicht zugeordneten Datenträger werden z. B. Menüoptionen zum Zuordnen zu einer Instanz und zum Löschen des Datenträgers angezeigt. |
{: caption="Tabelle 1. Details zu allen Datenträgern" caption-side="top"}

Standardmäßig werden 10 Datenträger in der Liste der Blockspeicherdatenträger angezeigt. Sie können diesen Standardwert ändern, indem Sie auf den Abwärtspfeil klicken und die Anzahl auf 20 oder 50 Datenträger erhöhen. Verwenden Sie die Pfeile in der rechten unteren Ecke, um zur nächsten Seite zu navigieren und wieder zurück zu navigieren.

## Details zu einem Blockspeicherdatenträger anzeigen
{: #view-vol-details}

Navigieren Sie zum Anzeigen von Details zu einem Blockspeicherdatenträger zu der Liste der Blockspeicherdatenträger und wählen Sie einen Datenträger aus.  Es werden die folgenden Informationen für einen einzelnen Datenträger angezeigt.

| Feld | Beschreibung |
|-------|-------------|
| Name  | Der Name des Datenträgers, den Sie beim Erstellen des Datenträgers angegeben haben. Klicken Sie auf das Stiftsymbol, um den Datenträgernamen zu bearbeiten. |
| Ressourcengruppe | Die bei der VPC-Einrichtung definierte Ressourcengruppe. Ressourcengruppen dienen zum Verwalten des Zugriffs auf Ressourcen, spielen bei Abrechnung und Überwachung jedoch keine Rolle. |
| Ressourcengruppe | Eine Ressourcengruppe auswählen, für die der Datenträger zugeordnet werden soll. Ressourcengruppen unterstützen Sie beim Organisieren von Ressourcen für Zugriffsberechtigungen und die Abrechnung. |
| Zuordnungstyp | "Daten" für einen sekundären Datenträger, der einer Instanz zugeordnet ist, und "Boot" für einen als Bootdatenträger zugeordneten Datenträger. Dieses Feld bleibt für Datenträger, die nicht zugeordnet sind, leer. |
| ID | Vom System generierte Datenträger-ID. |
| Erstellt | Vom System generiertes Datum, an dem der Datenträger erstellt wurde. |
| Standort | Die Verfügbarkeitszone in Ihrer Region. |
| Größe | Die Größe des von Ihnen angegebenen Datenträgers. |
| Profil | IOPS-Tier-Profil oder angepasstes IOPS-Profil. |
| Max. IOPS | Der maximale Wert für E/A-Operationen pro Sekunde für ein vordefiniertes IOPS-Tier oder der von Ihnen angegebene Wert für ein angepasstes IOPS-Profil. |
| Durchsatz | Die Leistung, die eine Platte liefern kann, gemessen in Gigabit/Sekunde (Gb/s).  Ausgerichtet am Datenträgerprofil wird der Durchsatz als Produkt aus dem IOPS-Wert und 16 KB (für die Blockgröße) berechnet. |
| Verschlüsselung | Vom Provider verwaltete Verschlüsselung oder benutzerverwaltete Verschlüsselung. |
{: caption="Tabelle 2. Datenträgerdetails" caption-side="top"}

Datenträger, die einer virtuellen Serverinstanz zugeordnet sind, werden auf der Seite **Datenträgerdetails** unter **Zugeordnete Instanzen** angezeigt.  Sie können auch [einen Datenträger einer Instanz zuordnen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Bei einem Datenträger, der einer Instanz zugeordnet ist, können Sie auch zu Informationen über die Instanz navigieren und dann zu einer Liste mit allen Blockspeicherdatenträgern zurückkehren.

## Details zu einem zugeordneten Blockspeicherdatenträger über die Seite mit den Instanzdetails anzeigen

Sie können Informationen zu einem zugeordneten Blockspeicherdatenträger auf der Seite **Details der virtuellen Serverinstanz** anzeigen:

1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Datenverarbeitung > Virtuelle Serverinstanzen** und wählen Sie eine Instanz aus.
1. Klicken Sie unter **Zugeordnete Blockspeicherdatenträger** auf den Namen eines Datenträgers, um die Seite mit den Details zu dem jeweiligen Datenträger anzuzeigen.

Möchten Sie Blockspeicherdatenträger lieber über die Befehlszeilenschnittstelle anzeigen? Informationen hierzu finden Sie unter [Blockspeicherdatenträger über die Befehlszeilenschnittstelle anzeigen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli).
{: tip}

## Weitere Schritte
{: #next-step-viewing-block-storage}

Erstellen Sie weitere Datenträger oder verwalten Sie die vorhandenen Blockspeicherdatenträger.

* [Blockspeicherdatenträger in der IBM Cloud-Konsole erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Blockspeicherdatenträger über die Benutzerschnittstelle verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
