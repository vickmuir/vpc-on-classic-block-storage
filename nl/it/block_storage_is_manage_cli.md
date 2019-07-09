---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# Gestione dei volumi di archiviazione blocchi utilizzando la CLI 
{: #managing-block-storage-cli}

Queste informazioni si applicano a {{site.data.keyword.cloud}} Virtual Private Cloud nell'ambiente dell'infrastruttura classica.
{: important}

## Prima di cominciare
{: #before-managing-block-storage-cli}

Assicurati di aver scaricato, installato e inizializzato i seguenti plugin CLI:

* CLI {{site.data.keyword.cloud_notm}}
* CLI API regionale {{site.data.keyword.cloud_notm}}

Per ulteriori informazioni, vedi i prerequisiti in [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Aggiorna il nome di un volume
{: #update-vol-name}

Per modificare un nome volume, specifica l'ID o il nome del volume e quindi indica un nuovo nome.

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

Esempio:

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

## Aggiorna un collegamento di volumi utilizzando la CLI
{: #update-vol-name-cli}

Puoi aggiornare il nome del collegamento di volumi e modificare l'impostazione di eliminazione automatica predefinita con il comando `instance-volume-attachment-update`.

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

Utilizza il parametro `--name` e specifica un nuovo nome per il collegamento di volumi.

Specifica `--auto-delete true` per eliminare automaticamente il volume quando elimini l'istanza a cui è collegato.

Esempio che mostra i dettagli per `Volume Attachment Instance Reference`:

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## Scollega un volume utilizzando la CLI
{: #detach-vol-attachment-cli}

Utilizza il comando `instance-volume-attachment-detach` per scollegare un volume da un'istanza ed eliminare il collegamento di volumi. Il volume di archiviazione blocchi non viene eliminato; puoi successivamente [collegarlo a un'altra istanza](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## Elimina un volume di archiviazione blocchi utilizzando la CLI
{: #delete-vol-cli}

Utilizza il comando `volume-delete` e specifica l'ID volume per eliminare un volume di archiviazione blocchi.

**Nota:** non puoi eliminare un volume di archiviazione blocchi attivo. Devi prima [scollegarlo dal server virtuale](#detach-vol-attachment-cli).

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

Esempio:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

Preferisci gestire i volumi di archiviazione blocchi utilizzando la console {{site.data.keyword.cloud}}? Per ulteriori informazioni, vedi [Gestione dei volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage).
{:tip}

## Passi successivi
{: #next-step-managing-block-storage-cli}

[Crea ulteriori volumi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

Per problemi con i volumi di archiviazione blocchi esistenti, potresti essere in grado di risolvere i problemi da solo. Per ulteriori informazioni, vedi [Risoluzione dei problemi per l'archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
