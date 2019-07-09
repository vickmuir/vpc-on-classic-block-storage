---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Esercitazione introduttiva 
{: #getting-started}

Questa esercitazione ti aiuta nella creazione di volumi {{site.data.keyword.block_storage_is_short}} su un VPC (Virtual Private Cloud).

## Prima di cominciare
{: #block-storage-before-you-begin}

Per iniziare, per prima cosa controlla il contenuto che può aiutarti con l'implementazione. Non hai esperienza con {{site.data.keyword.cloud}} e {{site.data.keyword.block_storage_is_short}}? Le seguenti informazioni potrebbero essere utili:

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [Informazioni su Block Storage per VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

Registrati per un account {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Registrazione a {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}.

## Passo 1 - Determina i tuoi requisiti di archiviazione
{: #determine-storage-requirements}

Stai eseguendo dei carichi di lavoro per finalità generiche con semplici requisiti di archiviazione? Oppure i tuoi carichi di lavoro sono ad uso intensivo di I/O che richiedono prestazioni e capacità elevate? Per ulteriori informazioni su come puoi determinare la capacità e le prestazioni, vedi [Prestazioni e capacità di Block Storage](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance). Vedi anche [Profili](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) per conoscere quale opzione di profilo IOPS può adattarsi meglio ai tuoi requisiti di archiviazione. 

Stai anche creando un'istanza del server virtuale? Vedi [come i profili del server virtuale si correlano ai profili di archiviazione](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage).

## Passo 2 - Dimensione e prezzo della tua archiviazione blocchi
{: #size-price-block-storage}

Seleziona un [profilo livello IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) per il tuo volume di archiviazione blocchi.  Facoltativamente, se hai dei prerequisiti di prestazioni ben definiti che non rientrano all'interno di un livello IOPS predefinito, scegli un [profilo IOPS personalizzato](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). 

Dopo aver scelto la dimensione e le prestazioni dei tuoi volumi di archiviazione blocchi, vedi le informazioni sui [Prezzi](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing) per calcolare i prezzi dei tuoi volumi e comprendere come avviene la fatturazione.

## Passo 3 - Accedi al tuo account {{site.data.keyword.cloud_notm}} 
{: block-storage-log-into-ibm-account}

Accesso al modulo d'ordine di {{site.data.keyword.block_storage_is_short}} dal [catalogo {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: external}. Utilizza il tuo ID IBM e la tua password.

## Passo 4 (facoltativo) -  Verifica l'accesso a {{site.data.keyword.vpc_short}}

Se vuoi creare un volume nel VPC (Virtual Private Cloud), devi prima [creare un VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console). Ignora questo passo se vuoi creare un volume autonomo all'esterno del VPC. Puoi successivamente richiedere l'accesso a {{site.data.keyword.vpc_short}} per accedere a un'istanza e collegare un volume di archiviazione blocchi che hai creato in modo indipendente. Per ulteriori informazioni su {{site.data.keyword.vpc_short}}, vedi l'[esercitazione introduttiva di VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Passo 5 - Crea i volumi di archiviazione blocchi

Inizia creando i tuoi volumi nella [console (IU) {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), utilizzando la [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) o l'[API {{site.data.keyword.vpc_short}}](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}. Per ulteriori informazioni sull'utilizzo di IBM Cloud Developer Tools per installare la CLI IBM Cloud, vedi [Introduzione alla CLI IBM Cloud Developer Tools](/docs/cli?topic=cloud-cli-getting-started).

## Passi successivi
{: #next-step-block-storage-getting-started}

Dopo aver creato la tua archiviazione blocchi, esplora altre opzioni:

* [Visualizza i dettagli sul volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Gestisci i tuoi volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
