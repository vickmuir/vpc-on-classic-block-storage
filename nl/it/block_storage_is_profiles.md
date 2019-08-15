---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Profili {{site.data.keyword.block_storage_is_short}} 
{: #block-storage-profiles}

Quando esegui il provisioning di volumi secondari di {{site.data.keyword.block_storage_is_short}} utilizzando la console {{site.data.keyword.cloud_notm}}, la CLI o l'API, specifica un profilo IOPS che si adatta meglio ai tuoi requisiti di archiviazione. I profili sono disponibili come tre livelli IOPS predefiniti o come IOPS personalizzati.  I livelli IOPS forniscono prestazioni IOPS/GB garantite per volumi con una capacità fino a 2 TB. Puoi anche specificare un profilo IOPS personalizzato e definire gli IOPS e la capacità di un volume all'interno di un intervallo.
{:shortdesc}

## Profili IOPS a livelli
{: #tiers}

L'archiviazione blocchi fornisce tre livelli IOPS predefiniti che puoi selezionare per specificare prestazioni ottimali per i tuoi carichi di lavoro di calcolo ed evitare colli di bottiglia. Puoi eseguire il provisioning di volumi nella tua zona di disponibilità con IOPS garantiti, come descritto nella seguente tabella:

| Livello IOPS | Carico di lavoro | Dimensione del volume | Numero massimo di IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | Carichi di lavoro generici - I carichi di lavoro che ospitano piccoli database per le applicazioni web o archiviano le immagini disco della macchina virtuale per un'hypervisor | Da 10 GB a 1 TB | Fino a 3.000 IOPS |
| | | Tra 1 TB e 2 TB | 3 IOPS/GB fino a 6.000 IOPS |
| 5 IOPS/GB | Carichi di lavoro ad alta intensità I/O - I carichi di lavoro caratterizzati da un'ampia percentuale di dati attivi, ad esempio i database transazionali e altri database sensibili alle prestazioni| Da 10 GB a 600 GB | Fino a 3.000 IOPS |
| | | Tra 600 GB e 2 TB | 5 IOPS/GB fino a 10.000 IOPS|
| 10 IOPS/GB | Carichi di lavoro di archiviazione impegnativi - I carichi di lavoro ad uso intensivo di dati creati dai database NoSQL, l'elaborazione dei dati per video, il machine learning e l'analisi | Da 10 GB a 300 GB | Fino a 3.000 IOPS |
| | | Tra 300 GB e 2 TB | 10 IOPS/GB fino a 20.000 IOPS |
{: caption="Tabella 1. Profili di livello IOPS e livelli di prestazioni per ogni profilo" caption-side="top"}

La velocità effettiva massima per tutti i livelli IOPS dell'archiviazione blocchi è 750 MB/s basata su una dimensione blocco di 16K

## Profilo IOPS personalizzato
{: #custom}

Gli IOPS personalizzati sono una buona opzione quando disponi di requisiti di prestazioni ben definiti che non rientrano in un intervallo IOPS predefinito. Puoi personalizzare gli IOPS specificando il numero totale di IOPS per il volume all'interno dell'intervallo per la dimensione del volume. Puoi eseguire il provisioning di volumi con IOPS compresi nell'intervallo 100 - 20.000.

La seguente tabella mostra gli intervalli IOPS disponibili basati sulla dimensione del volume.

| Dimensione volume (GB) | Intervallo IOPS |
|-------------|--------------|
| 10 -39   | 100 - 1.000 |
| 40 - 79 | 100 -2.000 |
| 80 - 99 | 100 - 4.000 |
| 100 - 499 | 100 - 6.000 |
| 500 - 999 | 100 - 10.000 |
| 1.000 - 1.999 | 100 - 20.000 |
{: caption="Tabella 2. IOPS disponibili in base alla dimensione del volume" caption-side="top"}

## Come i profili del server virtuale si correlano ai profili di archiviazione
{: #vsi-profiles-relate-to-storage}

I profili del server virtuale sono una combinazione di CPU virtuale e RAM che possono essere istanziati velocemente per avviare un'istanza del server virtuale.  Puoi selezionare tra [tre famiglie di profili](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)
in base ai tuoi requisiti di carico di lavoro.  Tali requisiti vanno dai carichi di lavoro comuni a carichi di lavoro ad uso intensivo di CPU e memoria.  

In modo simile, i profili di archiviazione (livelli IOPS o personalizzati) forniscono un intervallo di capacità e prestazioni per i volumi secondari.  Per impostazione predefinita,
un volume di avvio primario da 100 GB viene creato quando crei un'istanza del server virtuale.  Puoi anche creare e collegare dei volumi secondari.  
Quando crei un volume di dati secondario come parte della creazione dell'istanza, seleziona un profilo di archiviazione che meglio si adatta ai tuoi
requisiti di archiviazione per i tuoi carichi di lavoro di calcolo. In generale, quando aumentano i tuoi requisiti di calcolo, hai bisogno di maggiori prestazioni IOPS.  La seguente tabella mostra questa relazione.

| Profilo di archiviazione livello IOPS | Profilo del server virtuale |
|-----------------|------------------------|
| 3 IOPS/GB       | [Bilanciato](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) per carichi di lavoro comuni |
| 5 IOPS/GB       | [Calcolo](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) per richieste di CPU intensiva |
| 10 IOPS/GB      | [Memoria](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) per carichi di lavoro ad uso intensivo di memoria |
{: caption="Tabella 3. Correlazione dei profili di archiviazione blocchi con i profili di server virtuale" caption-side="top"}

## Visualizzazione dei profili IOPS
{: #view-iops-profiles}

Puoi visualizzare i profili IOPS disponibili tramite la console {{site.data.keyword.cloud_notm}}, la CLI o l'API.

### Utilizzo della console IBM Cloud
{: using-console-iops-profile}

 Quando [crei un volume di archiviazione blocchi dalla console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), seleziona **Tiers** dal menu a discesa.

 In alternativa, seleziona **Custom** e seleziona quindi un valore IOPS all'interno dell'intervallo di tale dimensione del volume. Fai clic sul link storage size per visualizzare una tabella di intervalli di dimensioni e IOPS.

 ### Utilizzo della CLI
 {: using-cli-iops-profiles}

 Per visualizzare l'elenco di profili disponibili utilizzando la CLI, immetti il seguente comando:
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### Utilizzo dell'API
{: using-api-iops-profiles}

La seguente richiesta API cURL richiama tutti i profili del volume.

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## Informazioni correlate

Per informazioni sui profili Bilanciato, Calcolo e Memoria per {{site.data.keyword.vsi_is_short}}, vedi [Profili](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).
