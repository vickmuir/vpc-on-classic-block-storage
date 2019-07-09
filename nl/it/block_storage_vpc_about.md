---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS, HPCS, Key Protect

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Informazioni su Block Storage per VPC
{: #block-storage-about}
[comment]: # (argomento della guida collegato)

{{site.data.keyword.block_storage_is_full}} (VPC) fornisce archiviazione dati montata sull'hypervisor e ad elevate prestazioni per le tue istanze del server virtuale di cui puoi eseguire il provisioning all'interno di un {{site.data.keyword.vpc_full}} (VPC). L'infrastruttura VPC fornisce un rapido ridimensionamento in più regioni e zone e ulteriori prestazioni e sicurezza. Per ulteriori informazioni su {{site.data.keyword.vpc_short}}, vedi [Informazioni su VPC (Virtual Private Cloud)](/docs/vpc-on-classic?topic=vpc-on-classic-about).
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} fornisce volumi di avvio primari e volumi di dati secondari. I volumi di avvio vengono automaticamente creati e collegati durante il provisioning dell'istanza. Anche i volumi di dati possono essere creati e collegati durante il provisioning dell'istanza oppure come dei volumi autonomi che puoi successivamente collegare a un'istanza. Per proteggere i tuoi dati, puoi utilizzare la tua chiave di crittografia o scegliere la crittografia gestita da IBM. I [profili livello IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) ti consentono di specificare un livello di prestazioni predefinito per i tuoi volumi. Oppure puoi scegliere un [profilo IOPS personalizzato](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e definire la tua capacità del volume e il tuo livello IOPS.

## Volumi di archiviazione blocchi per VPC
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} offre dei volumi di archiviazione dati al livello di blocco che possono essere collegati a un'istanza come un volume di avvio o dati. Puoi configurare fino a 750 volumi di archiviazione blocchi per regione. Puoi collegare diversi volumi di dati di archiviazione blocchi a una singola istanza per ulteriore capacità. Il numero di volumi che puoi collegare a un'istanza dipende da quante CPU virtuali contiene l'istanza. Per ulteriori informazioni, vedi [Limiti di collegamento del volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits).

### Volumi di avvio
{: #block-storage-vpc-boot-volumes}

Quando crei un'istanza, un volume di avvio da 100 GB viene automaticamente creato e collegato all'istanza. Il volume di avvio ha un numero massimo di IOPS di 3.000. Puoi crittografare il volume di avvio utilizzando le [tue chiavi di crittografia](#about-customer-managed-encrytion) o utilizzare [crittografia gestita dal provider](#about-provider-managed-encryption) predefinita. Un volume di avvio non può essere scollegato ed eliminato manualmente, ma viene eliminato quando elimini l'istanza.

### Volumi di dati secondari
{: #secondary-data-volumes}

I volumi di dati di archiviazione blocchi sono volumi secondari con un intervallo di capacità totale compreso tra 10 e 2000 GB. Il numero massimo di IOPS per i volumi di dati varia in base alla dimensione del volume e al profilo di livello IOPS che hai selezionato. Ad esempio, il numero massimo di IOPS per un volume di ambito generale fino a 1 TB è di 3.000 IOPS. Per ulteriori informazioni, vedi [Profili IOPS a livelli](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers).

Crea i volumi di dati come volumi autonomi oppure quando esegui il provisioning di un'istanza. I volumi autonomi sono nello stato scollegato finché non colleghi il volume a un'istanza. Quando crei un volume di dati come parte del provisioning di un'istanza, il volume viene automaticamente collegato all'istanza.  

I volumi di dati di archiviazione blocchi possono essere collegati a qualsiasi istanza disponibile nella tua regione, entro [alcuni limiti](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits). Questi volumi vengono scollegati per impostazione predefinita quando viene eliminata l'istanza. Lo scollegamento per impostazione predefinita consente a tuoi dati di perdurare anche dopo il ciclo di vita dell'istanza del server virtuale. Viene rimossa solo l'associazione del volume con l'istanza. Puoi eliminare i volumi di dati manualmente dopo che vengono scollegati oppure, quando crei un volume, puoi specificare che vengano [automaticamente scollegati ed eliminati](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete) quando viene eliminata l'istanza.

I volumi di dati vengono crittografati per impostazione predefinita con la crittografia gestita da IBM. Facoltativamente, puoi crittografare i volumi di dati utilizzando la [tua chiave di crittografia](#about-customer-managed-encrytion).

## Crittografia dei dati inattivi
{: #encryption}

{{site.data.keyword.cloud_notm}} prende sul serio la sicurezza e comprende l'importanza di poter crittografare i dati per tenerli al sicuro. Quando crei un volume autonomo o un volume come parte della creazione di un'istanza, puoi scegliere di proteggere i tuoi dati con la crittografia gestita dal provider IBM o di utilizzare le tue chiavi di crittografia.  

### Crittografia gestita dal provider
{: #about-provider-managed-encryption}

Per impostazione predefinita, tutti i volumi di avvio e di dati vengono crittografati con la crittografia gestita dal provider IBM. Non ci sono costi aggiuntivi per questo servizio o impatto sulle prestazioni. La crittografia gestita dal provider utilizza i seguenti protocolli standard del settore.

* Crittografia AES-256
* Le chiavi sono gestite internamente con il KMIP (Key Management Interoperability Protocol)  
* L'archiviazione è convalidata per FIPS PUB (Federal Information Processing Standard Publication) 140-2, FISMA (Federal Information Security Management Act) e HIPAA (Health Insurance Portability and Accountability Act). L'archiviazione viene anche convalidata per la conformità a PCI (Payment Card Industry), Basel II, California Security Breach Information Act (SB 1386) e alla direttiva sulla protezione dei dati dell'Unione europea 95/46/EC.

### Crittografia gestita dal cliente
{: #about-customer-managed-encrytion}

Puoi crittografare i volumi di archiviazione blocchi con le tue chiavi di crittografia. Per i volumi di dati, specifica la crittografia gestita dal cliente quando crei il volume. Per i volumi di avvio, puoi modificare le proprietà del volume di avvio durante la creazione dell'istanza e specificare la crittografia gestita dal cliente. Per le procedure, vedi [Creazione dei volumi di archiviazione blocchi con la crittografia gestita dal cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Con la crittografia gestita dal cliente, la tua chiave di crittografia viene caricata in un servizio di gestione delle chiavi ({{site.data.keyword.keymanagementservicelong_notm}} o {{site.data.keyword.hscrypto}}). L'infrastruttura VPC individua la chiave nell'istanza del servizio di gestione delle chiavi che hai precedentemente configurato e poi crittografa il volume. Per i prerequisiti e la procedura di configurazione monouso, vedi [Creazione dei volumi di archiviazione blocchi con la crittografia gestita dal cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Per ulteriori informazioni sulla creazione della crittografia gestita dal cliente per i volumi durante il provisioning dell'istanza del server virtuale, vedi [Crittografia gestita dal cliente per l'archiviazione blocchi](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys).

## Informazioni correlate

Per ulteriori informazioni sulla creazione e gestione delle istanze nel VPC, vedi [Informazioni su Virtual Servers for VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

Per iniziare a creare l'archiviazione blocchi per VPC, vedi [Creazione dei volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage).

{{site.data.keyword.block_storage_is_short}} fornisce delle funzioni univoche per il VPC e non è compatibile con l'archiviazione dell'infrastruttura classica. Se sei interessato a {{site.data.keyword.blockstoragefull}} sull'infrastruttura classica, vedi [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).
{:note}
