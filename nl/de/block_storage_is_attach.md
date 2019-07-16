---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, block storage volume, volume, volume attachment, virtual server instance, instance

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

# Blockspeicherdatenträger über die Benutzerschnittstelle zuordnen
{: #attaching-block-storage}

Wenn Sie einen Blockspeicherdatenträger für eine virtuelle Serverinstanz über die Benutzerschnittstelle erstellen, wird der Datenträger standardmäßig der Instanz zugeordnet. Wenn Sie die Zuordnung eines Datenträgers aufheben, steht er als nicht zugeordneter Datenträger für eine spätere erneute Zuordnung zur Verfügung. Diese verfügbaren Datenträger werden in der Liste der [gesamten Blockspeicherdatenträger](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols) angezeigt. Einer anderen Instanz können Sie den Datenträger über die Liste der gesamten Blockspeicherdatenträger oder beim Anzeigen von Details einer bestimmten Instanz zuordnen.{:shortdesc}

## Grenzwerte beim Zuordnen von Datenträgern
{: #vol-attach-limits}

Sie können zwar nicht mehrere Blockspeicherdatenträger gleichzeitig zu einer virtuellen Serverinstanz zuordnen, einer Instanz können jedoch im Rahmen der folgenden Grenzwerte mehrere verschieden Blockspeicherdatenträger zugeordnet werden:

* Instanzen mit weniger als 4 virtuellen CPUs können bis zu 4 sekundäre Blockspeicherdatenträger zusätzlich zum Bootdatenträger zugeordnet werden.
* Instanzen mit mindestens 4 virtuellen CPUs können bis zu 12 sekundäre Blockspeicherdatenträger zusätzlich zum Bootdatenträger zugeordnet werden.

## Blockspeicherdatenträger einer virtuellen Serverinstanz zuordnen
{: #attach}

Rufen Sie die Liste der gesamten Blockspeicherdatenträger auf und gehen Sie wie im Folgenden beschrieben vor. 

1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Speicher > Blockspeicherdatenträger für VPC**.
1. Klicken Sie in der Liste der Datenträger bei einem verfügbaren, nicht zugeordneten Datenträger auf die Punkte am Ende der Zeile. Daraufhin wird ein kontextspezifisches Aktionsmenü angezeigt.
1. Wählen Sie **Zu Instanz zuordnen** aus.
1. Wählen Sie in der Liste der verfügbaren Ressourcen eine Datenverarbeitungsressource (virtuelle Serverinstanz) aus und klicken Sie anschließend auf **Zuordnen**.
1. Auf der Seite mit den Datenträgerdetails werden Nachrichten angezeigt, die darauf hinweisen, dass der Datenträger derzeit zum Image zugeordnet wird. Nach Abschluss des Vorgangs wird der Imagename unter **Zugeordnete Instanzen** angezeigt.

Sie können einen Blockspeicherdatenträger auch über die Seite mit den Details zu einer virtuellen Serverinstanz zuordnen.

1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} für Virtual Private Cloud zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Datenverarbeitung > Virtuelle Serverinstanzen für VPC**.
1. Wählen Sie in der Liste der gesamten virtuellen Serverinstanzen eine Instanz aus. Wenn Blockspeicherdatenträger zugeordnet sind, werden diese Datenträger unter **Zugeordnete Blockspeicherdatenträger** aufgelistet.
1. Wählen Sie **Datenträger zuordnen** aus.
1. Wählen Sie in der Liste der verfügbaren Ressourcen einen Datenträger aus und klicken Sie auf **Zuordnen**. Auf der Seite mit den Instanzdetails werden Nachrichten angezeigt, die darauf hinweisen, dass der Datenträger derzeit zugeordnet wird. Nach Abschluss des Vorgangs wird die Liste **Zugeordnete Blockspeicherdatenträger** mit dem neuen Datenträger aktualisiert.

Sie können Blockspeicherdatenträger auch manuell über die Befehlszeilenschnittstelle zuordnen. Informationen hierzu finden Sie unter [Blockspeicherdatenträger über die Befehlszeilenschnittstelle zuordnen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
{: tip}

## Weitere Schritte
{: #next-step-attaching-block-storage}

Erstellen Sie zusätzliche Datenträger und verwalten Sie vorhandene Datenträger. Siehe dazu die folgenden Informationen.

* [Blockspeicherdatenträger in der IBM Cloud-Konsole erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Blockspeicherdatenträger über die Benutzerschnittstelle verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
