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

# Creazione dei volumi di archiviazione blocchi utilizzando la CLI
{: #creating-block-storage-cli}

Puoi creare dei volumi {{site.data.keyword.block_storage_is_full}} utilizzando l'interfaccia riga di comando (CLI).
{:shortdesc}

## Prima di cominciare
{: #before-creating-block-storage-cli}

Assicurati di aver scaricato, installato e inizializzato i seguenti plugin CLI:

* CLI {{site.data.keyword.cloud_notm}}
* Il plugin infrastructure-service

Per ulteriori informazioni, vedi i prerequisiti in [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Crea un volume di archiviazione blocchi utilizzando la CLI
{: #create-vol-cli}

Immetti il seguente comando.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Esempio:

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

La capacità, indicata in megabyte, può essere compresa nell'intervallo tra 10 e 2.000 GB.  I valori IOPS possono essere compresi tra 1.000 e 20.000 IOPS, a seconda della dimensione del volume. Se non specifichi un valore IOPS, viene utilizzata per impostazione predefinita la configurazione valida del profilo del volume. Per informazioni, vedi la tabella di [Intervalli IOPS basati sulla dimensione del volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).

L'ID volume nel precedente esempio viene utilizzato quando colleghi l'archiviazione blocchi a un'istanza del server virtuale, visualizzi i dettagli del volume di archiviazione blocchi ed elimini i volumi.

Preferisci creare dei volumi di archiviazione blocchi dalla console {{site.data.keyword.cloud}}? Per informazioni, vedi [Creazione dei volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
{: tip}

## Passi successivi
{: #next-step-creating-block-storage-cli}

[Collega un volume di archiviazione blocchi (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
