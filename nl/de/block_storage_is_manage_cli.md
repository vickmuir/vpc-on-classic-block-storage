---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Blockspeicherdatenträger über die Befehlszeilenschnittstelle verwalten
{: #managing-block-storage-cli}

Sie können {{site.data.keyword.block_storage_is_short}} über die Befehlszeilenschnittstelle (CLI) verwalten. Aktualisieren Sie einen Datenträgernamen oder eine Datenträgerzuordnung, heben Sie die Zuordnung für einen Datenträger auf oder löschen Sie einen Datenträger.
{:shortdesc}

## Vorbereitungen
{: #before-managing-block-storage-cli}

1. Stellen Sie sicher, dass Sie die folgenden Plug-ins für die Befehlszeilenschnittstelle heruntergeladen, installiert und initialisiert haben:
    * {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle
    * Infrastrukturservice-Plug-in

   Weitere Informationen finden Sie in den [Referenzinformationen zur {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle für VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference). 
   
   Wenn Sie das VPC-Infrastruktur-Plug-in zum ersten Mal installieren, müssen Sie für die Zielgeneration 'gen 1' festlegen: `ibmcloud is target --gen 1`.
   {:important}
   
2. Stellen Sie sicher, dass bereits eine [{{site.data.keyword.vpc_short}}-Instanz erstellt](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started) wurde. 

## Namen eines Datenträgers aktualisieren
{: #update-vol-name}

Geben Sie zum Ändern eines Datenträgernamens den Datenträgernamen oder die Datenträger-ID gefolgt von dem neuen Namen an.

```bash
ibmcloud is volume-update DATENTRÄGER-ID [--name NEUER_NAME] [--json]
```

Beispiel:

```bash
$ ibmcloud is volume-update 933c8781-f7f5-4a8f-8a2d-3bfc711788ee --name demo-volume-update
Updating volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount 01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo-volume-update
Capacity                                100
IOPS                                    1000
Profile                                 5iops-tier
Encryption                              -
Encryption                              provider managed
Status                                  available
Created                                 2019-05-20 10:09:28
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Zone                                    us-south-2
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Volume Attachment Instance Reference    none
```
{: screen}

## Datenträgerzuordnung über die Befehlszeilenschnittstelle aktualisieren
{: #update-vol-name-cli}

Mit dem Befehl `instance-volume-attachment-update` können Sie den Namen einer Datenträgerzuordnung aktualisieren und die Standardeinstellung für automatisches Löschen ändern.

```bash
ibmcloud is instance-volume-attachment-update INSTANZ-ID ID_DER_DATENTRÄGERZUORDNUNG [--name NEUER_NAME] [--auto-delete true | false] [--json]
```

Geben Sie mit dem Parameter `-- name` einen neuen Namen für die Datenträgerzuordnung an.

Geben Sie mit `-- auto-delete true` an, dass der Datenträger automatisch gelöscht werden soll, wenn die Instanz, der der Datenträger zugeordnet ist, gelöscht wird.

Beispiel mit Details für `Datenträgerzuordnungs-Instanz-Referenz`:

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## Datenträgerzuordnung über die Befehlszeilenschnittstelle aufheben
{: #detach-vol-attachment-cli}

Mit dem Befehl `instance-volume-attachment-detach` können Sie die Zuordnung eines Datenträgers zu einer Instanz aufheben und die Datenträgerzuordnung löschen. Der Blockspeicherdatenträger wird nicht gelöscht. Sie können diesen Datenträger bei Bedarf [einer anderen Instanz zuordnen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).

```bash
ibmcloud is instance-volume-attachment-detach INSTANZ-ID ID_DER_DATENTRÄGERZUORDNUNG [-f, --force]
```

## Blockspeicherdatenträger über die Befehlszeilenschnittstelle löschen
{: #delete-vol-cli}

Mit dem Befehl `volume-delete` können Sie einen Blockspeicherdatenträger mit der angegebenen Datenträger-ID bzw. dem angegebenen Namen löschen.

**Hinweis:** Aktive Blockspeicherdatenträger können nicht gelöscht werden. Sie müssen zunächst die [Datenträgerzuordnung zum virtuellen Server aufheben](#detach-vol-attachment-cli).

```bash
ibmcloud is volume-delete (DATENTRÄGERNAME | DATENTRÄGER-ID) [-f, --force]
```

Beispiel:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

Möchten Sie Blockspeicherdatenträger lieber über die {{site.data.keyword.cloud}}-Konsole verwalten? Informationen hierzu finden Sie unter [Blockspeicherdatenträger verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage).
{:tip}

## Weitere Schritte
{: #next-step-managing-block-storage-cli}

[Erstellen Sie weitere Datenträger über die Befehlszeilenschnittstelle](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

Probleme mit vorhandenen Blockspeicherdatenträgern können Sie möglicherweise selbst eingrenzen und beheben. Weitere Informationen hierzu finden Sie unter
[Fehlerbehebung für Blockspeicher](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
