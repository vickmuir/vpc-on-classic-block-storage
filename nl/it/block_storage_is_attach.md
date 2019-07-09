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

# Collegamento di un volume di archiviazione blocchi utilizzando l'IU
{: #attaching-block-storage}

Quando crei un volume di archiviazione blocchi per un'istanza del server virtuale dall'IU, il volume viene collegato all'istanza per impostazione predefinita. Quando scolleghi un volume, rimane come un volume scollegato che puoi successivamente ricollegare.  Questi volumi disponibili vengono visualizzati nell'elenco di [tutti i volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). Puoi collegare il volume a un'altra istanza dall'elenco di tutti i volumi di archiviazione blocchi o quando visualizzi i dettagli su una particolare istanza.
{:shortdesc}

## Limiti di collegamento del volume
{: #vol-attach-limits}

Anche se colleghi solo un volume di archiviazione blocchi a un'istanza del server virtuale alla volta, puoi collegare diversi volumi di archiviazione blocchi differenti a una singola istanza, con i seguenti limiti:

* Le istanze con meno di 4 CPU virtuali possono collegare fino a 4 volumi secondari di archiviazione blocchi, più un volume di avvio.
* Le istanze con 4 o più CPU virtuali possono collegare fino a 12 volumi secondari di archiviazione blocchi, più un volume di avvio.

## Collega un volume di archiviazione blocchi a un'istanza del server virtuale
{: #attach}

Dall'elenco di tutti i volumi di archiviazione blocchi, segui questa procedura.

1. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Nell'elenco di volumi, fai clic sui puntini di sospensione alla fine della riga di un volume disponibile e scollegato.  Viene visualizzato un menu delle azioni specifico per il contesto.
1. Seleziona **Attach to instance**.
1. Seleziona una risorsa di calcolo (istanza del server virtuale) dall'elenco di risorse disponibili e fai quindi clic su **Attach**.
1. I messaggi visualizzati nella pagina dei dettagli del volume indicano che il volume viene collegato all'immagine.  Una volta completato, il nome dell'immagine viene visualizzato in **Attached instances**.

Puoi anche collegare un volume di archiviazione blocchi dalla pagina dei dettagli dell'istanza del server virtuale.

1. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Compute > Virtual server instances for VPC.**.
1. Seleziona un'istanza dall'elenco di tutte le istanze del server virtuale. Se esistono dei volumi di archiviazione blocchi collegati, li vedrai elencati in **Attached block storage volumes**.
1. Seleziona **Attach volume**.
1. Seleziona un volume dall'elenco di risorse disponibili e fai clic su **Attach**. I messaggi visualizzati nella pagina dei dettagli dell'istanza indicano che il volume viene collegato.  Una volta completato, l'elenco **Attached block storage volumes** viene aggiornato in modo da includere il nuovo volume.

Puoi anche collegare manualmente i volumi di archiviazione blocchi utilizzando la CLI. Per informazioni, vedi [Collegamento dei volumi di archiviazione blocchi (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
{: tip}

## Passi successivi 
{: #next-step-attaching-block-storage}

Crea ulteriori volumi e gestisci quelli esistenti. Vedi le seguenti informazioni.

* [Creazione dei volumi di archiviazione blocchi nella console IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gestione dei volumi di archiviazione blocchi utilizzando l'IU](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
