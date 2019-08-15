---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, CLI, block storage volume, volume, volume attachment, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Collegamento di un volume di archiviazione blocchi utilizzando la CLI
{: #attaching-block-storage-cli}

Un collegamento di volumi connette un volume {{site.data.keyword.block_storage_is_short}} a un'istanza del server virtuale. Ogni istanza può avere [molti collegamenti di volumi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits), ma un singolo collegamento di volumi connette un volume a un'istanza.
{:shortdesc}

## Prima di cominciare
{: #before-attaching-block-storage-cli}

1. Assicurati di aver scaricato, installato e inizializzato i seguenti plugin CLI:
    * CLI {{site.data.keyword.cloud_notm}}
    * Il plugin infrastructure-service

   Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}}CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Quando installi il plugin vpc-infrastructure per la prima volta, devi impostare la generazione di destinazione su gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assicurati di aver già [creato un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Collega un volume di archiviazione blocchi utilizzando la CLI
{: #attach-block-storage-cli}

Per collegare un volume a un'istanza del server virtuale nel gruppo di risorse correnti, esegui questo comando.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` è il nome che hai fornito per il collegamento di volumi e INSTANCE_ID è l'ID della VSI.

L'ID volume (`VOLUME_ID`) specifica il volume che stai collegando.

Specifica `--auto-delete true` se vuoi che il volume venga automaticamente eliminato quando viene eliminata la VSI.

Per visualizzare un elenco di istanze del server virtuale disponibili, esegui il comando `ibmcloud is instances`.

Esempio:

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.xxx.xx.xx    -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.xxx.xx.x     -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             192.xxx.xxx.xx   -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             192.xxx.xxx.xxx  -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## Mostra i dettagli di un volume collegato a un'istanza del server virtuale
{: #show-details-attached-vol}

Dopo aver collegato un volume, puoi visualizzare i dettagli specificando l'ID istanza e l'ID collegamento di volumi nel comando `instance-volume-attachment`.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## Elenca tutti i collegamenti di volumi di un'istanza del server

Utilizza il comando `instance-volume-attachments` e specifica l'ID istanza per visualizzare tutti i collegamenti di volumi per un'istanza.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

Preferisci utilizzare la console {{site.data.keyword.cloud}}? Per informazioni su come i volumi vengono collegati nella console, vedi [Collegamento dei volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).
{:tip}

## Crea un JSON di collegamenti volumi
{: #volume_attachment_json}

Quando esegui il provisioning di un'istanza del server virtuale utilizzando la CLI e crei un volume di archiviazione blocchi come parte del processo, devi specificare un JSON di collegamento volumi. Il JSON di collegamento volumi, specificato nel comando o come un file, definisce i parametri del volume. Quando [crei un'istanza](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) e specifichi il parametro `--volume-attach`, specifica il JSON del volume. Ad esempio, `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

Questo è un JSON di collegamento volumi di esempio che definisce un volume personalizzato:

```
[
    {
        "name": "myvolume-attachment",
        "delete_volume_on_instance_delete": true,
        "volume": {
            "name": "myvolume",
            "capacity": 100,
            "iops": 1000,
            "profile": {
                "name": "custom"
            }
        }
    }
]
```
{: screen}

## Passi successivi
{: #next-step-attaching-block-storage-cli}

Crea ulteriori volumi e gestisci quelli esistenti.  Vedi le seguenti informazioni.

* [Crea un volume di archiviazione blocchi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [Gestione dei volumi di archiviazione blocchi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
