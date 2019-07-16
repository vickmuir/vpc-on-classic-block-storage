---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Blockspeicherdatenträger über die Befehlszeilenschnittstelle erstellen
{: #creating-block-storage-cli}

Sie können {{site.data.keyword.block_storage_is_full}}-Datenträger über die Befehlszeilenschnittstelle (Command Line Interface - CLI) erstellen.{:shortdesc}

## Vorbereitungen
{: #before-creating-block-storage-cli}

Stellen Sie sicher, dass Sie die folgenden Plug-ins für die Befehlszeilenschnittstelle heruntergeladen, installiert und initialisiert haben:

* {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle
* Infrastrukturservice-Plug-in

Weitere Informationen finden Sie im Abschnitt zu den Voraussetzungen in der [Referenz zu IBM Cloud CLI for VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Blockspeicherdatenträger über die Befehlszeilenschnittstelle erstellen
{: #create-vol-cli}

Führen Sie den folgenden Befehl aus.

```bash
ibmcloud is volume-create DATENTRÄGERNAME PROFILNAME ZONENNAME [--encryption-key VERSCHLÜSSELUNGSSCHLÜSSEL] [--capacity KAPAZITÄT] [--iops IOPS] [--resource-group-id RESSOURCENGRUPPEN-ID | --resource-group-name RESSOURCENGRUPPENNAME] [--json]
```

Beispiel:

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Die in Megabyte angegebene Kapazität kann zwischen 10 und 2.000 GB liegen. Die IOPS-Werte können je nach Datenträgergröße 1.000 bis 20.000 E/A-Operationen pro Sekunde betragen. Wenn Sie keinen IOPS-Wert angeben, wird standardmäßig die für das Datenträgerprofil gültige Konfiguration festgelegt. Informationen hierzu finden Sie in der Tabelle der [an der Datenträgergröße ausgerichteten IOPS-Bereiche](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).

Die Datenträger-ID im zuvor genannten Beispiel wird verwendet, wenn Blockspeicher zu einer virtuellen Serverinstanz zugeordnet wird, Details eines Blockspeicherdatenträgers anzuzeigen werden oder Datenträger gelöscht werden.

Sie möchten Blockspeicherdatenträger lieber über die {{site.data.keyword.cloud}}-Konsole erstellen? Informationen hierzu finden Sie unter [Blockspeicherdatenträger erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
{: tip}

## Weitere Schritte
{: #next-step-creating-block-storage-cli}

[Blockspeicherdatenträger über die Befehlszeilenschnittstelle zuordnen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
