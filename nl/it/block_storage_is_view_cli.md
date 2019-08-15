---

copyright:
  years: 2019
lastupdated: "2019-07-03"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

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

# Visualizzazione dei volumi di archiviazione blocchi utilizzando la CLI
{: #viewing-block-storage-cli}

Visualizza i dettagli su un volume {{site.data.keyword.block_storage_is_short}} o le informazioni di riepilogo su tutti i volumi dalla CLI.
{:shortdesc}

## Prima di cominciare
{: #before-viewing-block-storage-cli}

1. Assicurati di aver scaricato, installato e inizializzato i seguenti plugin CLI:
    * CLI {{site.data.keyword.cloud_notm}}
    * Il plugin infrastructure-service

   Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}}CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Quando installi il plugin vpc-infrastructure per la prima volta, devi impostare la generazione di destinazione su gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assicurati di aver già [creato un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Visualizza i dettagli su un volume di archiviazione blocchi utilizzando la CLI
{: #viewvol-cli}

Specifica questo comando per mostrare i dettagli su un volume.

```bash
ibmcloud is volume VOLUME_ID [--json]
```

Esempio:

Questo esempio utilizza l'ID volume per mostrare i dettagli del volume.

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Se il tuo volume è collegato a un'istanza del server virtuale, vengono visualizzati anche il nome e l'ID dell'istanza e del collegamento di volumi.

## Visualizza tutti i volumi di archiviazione blocchi utilizzando la CLI
{: #viewall-vol-cli}

Immetti questo comando per elencare le informazioni di riepilogo su tutti i volumi:

```bash
ibmcloud is volumes [--json]
```

Esempio:

Il seguente esempio mostra tutti i volumi per tutti i gruppi di risorse nella tua zona di disponibilità.  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

Specificando l'ID o il nome del gruppo di risorse filtri l'elenco di volumi che appartengono a un gruppo di risorse. Quando ometti questo parametro, per impostazione predefinita vengono selezionati tutti i gruppi di risorse. Puoi anche visualizzare tutti i volumi in una particolare zona di disponibilità.

Per impostazione predefinita, vengono visualizzati i primi 25 volumi per pagina.

## Visualizza i dettagli su un collegamento di volumi utilizzando la CLI
{: #viewvol-attachment-cli}

Immetti questo comando per visualizzare i dettagli di un collegamento di volumi a un'istanza del server virtuale:

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

Specifica un ID istanza e un ID collegamento di volumi.  Facoltativamente, esporta i dettagli in formato JSON.

## Visualizza i dettagli su tutti i collegamenti di volumi utilizzando la CLI

Immetti questo comando per visualizzare tutti i collegamenti di volumi per un'istanza del server virtuale.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## Visualizza i profili del volume utilizzando la CLI
{: #viewvol-profiles-cli}

Immetti questo comando per elencare tutti i profili del volume disponibili nella tua regione.

```bash
ibmcloud is volume-profiles [--json]
```

Esempio:

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## Visualizza uno specifico profilo del volume utilizzando la CLI
{: #viewvol-profile-cli}

Immetti questo comando per visualizzare uno specifico profilo del volume nella tua regione.

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

I valori per PROFILE_NAME sono 10iops-tier, 5iops-tier, general-purpose e custom.

Esempio:

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

Preferisci utilizzare la console {{site.data.keyword.cloud}} per visualizzare i tuoi volumi di archiviazione blocchi? Per informazioni, vedi [Visualizzazione dei volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage).
{: tip}

## Passi successivi
{: #next-step-viewing-block-storage-cli}

Crea ulteriori volumi o gestisci i tuoi volumi di archiviazione blocchi esistenti.

* [Creazione dei volumi di archiviazione blocchi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [Gestione dei volumi di archiviazione blocchi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
