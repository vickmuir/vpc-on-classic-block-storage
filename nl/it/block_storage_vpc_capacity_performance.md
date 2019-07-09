---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

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

# Prestazioni e capacità di Block Storage
{: #capacity-performance}

La scelta del livello di prestazioni e della dimensione del volume di archiviazione blocchi ottimali per i tuoi carichi di lavoro è importante. Quando esegui il provisioning dell'archiviazione blocchi dall'IU o dalla CLI, puoi scegliere la dimensione del tuo volume e il livello di prestazioni.

### Capacità
{: #block-storage-vpc-capacity}

Puoi specificare da 10 a 2000 GB (2 TB) di capacità per volume di dati di archiviazione blocchi in incrementi da 1 GB. La capacità del volume totale viene determinata quando selezioni un [profilo IOPS](#iops-profiles). I volumi di avvio sono da 100 GB.

### Profili IOPS
{: #iops-profiles}

Quando esegui il provisioning di volumi {{site.data.keyword.block_storage_is_short}}, specifica un [profilo IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) che meglio si adatta ai tuoi requisiti di archiviazione. I profili sono disponibili come tre livelli IOPS predefiniti o come IOPS personalizzati. I [livelli IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) forniscono prestazioni IOPS/GB garantite per volumi con una capacità fino a 2 TB. Puoi anche specificare un profilo [IOPS personalizzato](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e definire gli IOPS e la capacità di un volume all'interno di un intervallo. Utilizza la console {{site.data.keyword.cloud_notm}}, la CLI o l'API per specificare un profilo.

## Come la dimensione blocco influenza le prestazioni
{: #how-block-size-affects-performance}

IOPS è basato su una dimensione di blocco di 16 KB con un carico di lavoro casuale al 50% e con lettura/scrittura al 50/50. Un blocco di 16 KB è l'equivalente di una scrittura sul volume. La velocità effettiva di base viene determinata dalla quantità di IOPS moltiplicata per la dimensione di blocco di 16 KB. Maggiori sono gli IOPS che specifichi e maggiore è la velocità effettiva. La velocità effettiva massima per un volume di archiviazione blocchi è 750 MB/s.

La dimensione di blocco che scegli per la tua applicazione influenza direttamente le prestazioni di archiviazione. Se la dimensione di blocco è più piccola di 16 KB, il limite di IOPS viene raggiunto prima del limite della velocità effettiva. Al contrario, se la dimensione di blocco è più grande di 16 KB, il limite della velocità effettiva viene raggiunto prima del limite di IOPS. La seguente tabella fornisce alcuni esempi di come la dimensione di blocco e gli IOPS influenzino la velocità effettiva.

|Dimensione blocco (KB)| IOPS | Velocità effettiva (MB/s) |
|-----------------|------|-------------------|
|4 (tipica per Linux)|1.000| 4 |
|8 (tipica per Oracle)|1.000| 8 |
| 16 |1.000| 16 |
|32 (tipica per SQL Server)| 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="La tabella 1 mostra degli esempi di come la dimensione di blocco e gli IOPS influenzino la velocità effettiva.<br/Dimensione IO media x IOPS = Velocità effettiva in MB/s." caption-side="top"}>
