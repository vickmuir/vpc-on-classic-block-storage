---

copyright:
  years: 2019
lastupdated: "2019-07-11"

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

# Blockspeicherdatenträger über die Benutzerschnittstelle verwalten
{: #managing-block-storage}

Sie können {{site.data.keyword.block_storage_is_short}} über die Benutzerschnittstelle verwalten. Heben Sie die Zuordnung eines Datenträgers zu einer virtuellen Serverinstanz auf, übertragen Sie einen Datenträger von einer Instanz zu einer anderen, ordnen Sie einen bereits zuvor zugeordneten Datenträger zu, benennen Sie einen Datenträger um, legen Sie das automatische Löschen von Datenträgern fest, löschen Sie einen Datenträger manuell oder weisen Sie Zugriffsberechtigungen für einen Datenträger zu.
{:shortdesc}

## Zuordnung eines Blockspeicherdatenträgers zu einer virtuellen Serverinstanz aufheben
{: #detach}

Sie können die Zuordnung eines Blockspeicherdatenträgers aufheben, der einer virtuellen Serverinstanz zugeordnet ist.  Durch das Aufheben der Zuordnung wird der Datenträger für eine Verwendung durch eine andere Instanz freigegeben.

Gehen Sie wie folgt vor, um die Zuordnung eines Datenträgers aufzuheben:

1. Navigieren Sie zur Liste aller Blockspeicherdatenträger. Rufen Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud das **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicher** auf.
1. Suchen Sie den Datenträger und klicken Sie dann auf die Punkte (...) am Ende der Tabellenzeile. Daraufhin wird ein Kontextmenü angezeigt.
1. Klicken Sie im Menü auf **Zuordnung zu Instanz aufheben**.
1. Klicken Sie zur Bestätigung im Popup-Fenster auf **Zuordnung von Instanz aufheben**.

Sie können stattdessen auch auf einen einzelnen Datenträger in der Liste der Blockspeicherdatenträger klicken und zu der Seite **Datenträgerdetails** für diesen Datenträger navigieren. Klicken Sie unter **Zugeordnete Instanzen** auf das Minuszeichen neben der virtuellen Serverinstanz, um die Zuordnung des Datenträgers zu dieser Instanz aufheben.

## Blockspeicherdatenträger von einer virtuellen Serverinstanz zu einer anderen Instanz zu übertragen
{: #transfer}

Gehen Sie wie folgt vor, um einen Blockspeicherdatenträger zu einer anderen virtuelle Serverinstanz zu übertragen:

1. [Heben Sie die Zuordnung des Datenträgers zu der virtuellen Serverinstanz auf](#detach).
1. Navigieren Sie zu der virtuellen Serverinstanz, zu der der Datenträger übertragen werden soll. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Datenverarbeitung > Virtuelle Serverinstanzen**.
1. Wählen Sie einen virtuellen Server in der Liste aus.
1. Klicken Sie unter 'Zugeordneter Speicher' auf das Pluszeichen, um einen Datenträger hinzuzufügen. Daraufhin werden alle Blockspeicherdatenträger angezeigt.
1. Wählen Sie in der Liste der Datenträger den Datenträger aus, dessen Zuordnung Sie zuvor aufgehoben haben.

## Zuvor zugeordneten Blockspeicherdatenträger zuordnen
{: #reattach}

Blockspeicherdatenträger werden standardmäßig beim Erstellen einer neuen virtuellen Serverinstanz zugeordnet.  Wenn Sie die Zuordnung eines Datenträgers zu einer Instanz aufheben, zählt der Datenträger als nicht zugeordneter Datenträger und wird in der Liste der [Blockspeicherdatenträger](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols) angezeigt. Sie können den Datenträger von der Liste der Blockspeicherdatenträger aus einem anderen Image zuordnen.

1. Navigieren Sie zur Liste aller Blockspeicherdatenträger. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicher**.
1. Suchen Sie den Datenträger und klicken Sie dann auf die Punkte (...) am Ende der Tabellenzeile. Daraufhin wird ein Kontextmenü angezeigt.
1. Klicken Sie im Menü auf **Zu Instanz zuordnen**.
1. Wählen Sie eine verfügbare virtuelle Serverinstanz aus.
1. Bestätigen Sie Ihre Auswahl.

## Blockspeicherdatenträger umbenennen
{: #rename}

Sie können den Namen eines vorhandenen Datenträgers ändern, um einen aussagefähigeren Namen verwenden zu können.

1. Navigieren Sie zur Liste aller Blockspeicherdatenträger. Wählen Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicher** aus.
1. Suchen Sie den Datenträger und klicken Sie dann auf den Namen des Datenträgers, um zur Seite 'Datenträgerdetails' zu gelangen.
1. Klicken Sie auf das Stiftsymbol neben dem Namen des Datenträgers und bearbeiten Sie den Datenträgernamen.
1. Bestätigen Sie die Namensänderung.

## Blockspeicherdatenträger löschen
{: #delete}

Durch das Löschen eines Blockspeicherdatenträgers werden die zugehörigen Daten vollständig entfernt. Der Datenträger kann nicht wiederhergestellt werden.

Es ist nicht möglich, einen aktiven Blockspeicherdatenträger zu löschen. [Heben Sie vor dem Löschen die Zuordnung des Datenträgers zum virtuellen Server auf](#detach) und gehen Sie dann wie folgt vor:

1. Navigieren Sie zur Liste aller Blockspeicherdatenträger. Rufen Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud das **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicher** auf.
1. Suchen Sie den Datenträger, den Sie löschen möchten, und klicken Sie dann auf die Punkte am Ende der Tabellenzeile. Daraufhin wird ein Kontextmenü angezeigt.
1. Klicken Sie im Menü auf **Löschen**.
1. Bestätigen Sie die Löschanforderung.

## Automatisches Löschen von Blockspeicherdatenträgern für Daten
{: #auto-delete}

Mit der Funktion für automatisches Löschen können Sie festlegen, dass ein Blockspeicherdatenträger für Daten automatisch gelöscht wird, wenn Sie die Instanz löschen, der der Datenträger zugeordnet ist. Diese Funktion kann nicht auf Bootdatenträger angewendet werden und ist standardmäßig inaktiviert.

Führen Sie die folgenden Schritte aus, um das automatische Löschen für einen vorhandenen Blockspeicherdatenträger zu aktivieren, der einer Instanz zugeordnet ist:

1. Suchen Sie die virtuelle Serverinstanz, der der Datenträger zugeordnet ist. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Datenverarbeitung > Virtuelle Serverinstanzen**.
1. Wählen Sie unter **Zugeordnete Blockspeicherdatenträger** einen Datenträger aus.
1. Klicken Sie im Popup-Menü auf die Schaltfläche 'Automatisch löschen', um diese Funktion zu aktivieren.
1. Bestätigen Sie Ihre Auswahl.

Alternativ dazu können Sie auch beginnen, indem Sie einen Datenträger in der Liste der Blockspeicherdatenträger (**Speicher > Blockspeicher**) auswählen.

Informationen zum Aktivieren des automatischen Löschens für einen neuen Datenträger beim Erstellen einer Instanz finden Sie unter [Blockspeicherdatenträger beim Erstellen einer neuen Instanz erstellen und zuordnen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi).

## Zugriff auf einen Blockspeicherdatenträger zuordnen
{: #assign-volume-access}

Als Benutzer mit Administratorberechtigungen können Sie einen Benutzerzugriff auf Datenträgerebene für den {{site.data.keyword.block_storage_is_short}}-Service zuordnen. In der folgenden Tabelle sind die Informationen aufgeführt, die Sie in der IAM-Benutzerschnittstelle ([Identity and Access Management)](/docs/iam?topic=iam-account_setup#assigning-access) angeben müssen.

| IAM-Feld | Aktion |
|--------|-------------|
| Services | Wählen Sie **Infrastrukturservices** aus. |
| Ressourcentyp | Wählen Sie **Block Storage for VPC** aus. |
| Datenträger-ID | Geben Sie die [Datenträger-ID](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) ein, um den Zugriff auf einen bestimmten Datenträger zuzuordnen. |
| Rollen auswählen | Ordnen Sie Plattformzugriffsrollen. Im Allgemeinen wird die Rolle 'Operator' zugeordnet. |
{: caption="Tabelle 1. Informationen für IAM" caption-side="top"}

Weitere Informationen finden Sie in den [Bewährte Verfahren für die Zuweisung von Zugriff](/docs/iam?topic=iam-account_setup#account_setup). Weitere Informationen zum vollständigen IAM-Ablauf, der das Einladen von Benutzern zu Ihrem Konto und das Zuweisen von Cloud IAM-Zugriff beinhaltet, finden Sie im [IAM-Einführungstutorial](/docs/iam?topic=iam-getstarted#getstarted).

## Status von Blockspeicherdatenträgern
{: #status}

In der folgenden Tabelle werden die Statusangaben angezeigt, die beim Erstellen, Anzeigen oder Verwalten von Blockspeicherdatenträgern erscheinen können.

| Status | Bedeutung |
|--------|-------------|
| Verfügbar | Ein Datenträger wurde erfolgreich abgerufen. |
| | Ein Datenträger ist verfügbar und kann einer Instanz zugeordnet werden. |
| | Der zugeordnete Datenträger steht für Daten zur Verfügung. |
| | Ein Bootdatenträger ist verfügbar. |
| Fehlgeschlagen    | Die Datenträgererstellung ist fehlgeschlagen. |
| | Sämtliche Datenträger in einer Region konnten nicht abgerufen werden. |
| | Ein Datenträger mit der angegebenen Datenträger-ID wurde nicht gefunden. |
| | Ein Datenträger konnte nicht gelöscht werden. |
| Anstehend | Ein Datenträger wird erstellt. |
| | Ein Datenträger wird einer Instanz zugeordnet. |
| Löschvorgang anstehend | Ein Datenträger wird derzeit gelöscht. |
{: caption="Tabelle 2. Blockspeicherstatusangaben" caption-side="top"}

Möchten Sie Blockspeicherdatenträger lieber über die Befehlszeilenschnittstelle verwalten? Informationen hierzu finden Sie unter [Blockspeicherdatenträger über die Befehlszeilenschnittstelle verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli).
{: tip}

## Weitere Schritte
{: #next-step-managing-block-storage}

Sie können [zusätzliche Datenträger erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

Probleme mit vorhandenen Blockspeicherdatenträgern können Sie Fehler möglicherweise selbst beheben und Probleme beseitigen. Weitere Informationen hierzu finden Sie unter [Fehlerbehebung für Blockspeicher](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
