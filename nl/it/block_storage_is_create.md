---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Creazione dei volumi di archiviazione blocchi nella console {{site.data.keyword.cloud_notm}}
{: #creating-block-storage}
[comment]: # (argomento della guida collegato)

Puoi creare un volume {{site.data.keyword.block_storage_is_short}}quando crei un'istanza del server virtuale oppure creare un volume autonomo da collegare successivamente a un'istanza.
{:shortdesc}

Prima di iniziare, assicurati di aver [creato un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Crea e collega un volume di archiviazione blocchi quando crei una nuova istanza
{: #create-from-vsi}

1. Crea un'istanza. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Compute > Virtual server instances > New instance**.
1. [Configura la tua istanza del server virtuale](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers). In **Attached block storage volumes**, seleziona **New block storage volume**.
1. Immetti le informazioni descritte nella seguente tabella.  Quando terminato, fai clic su **Create volume**.

| Campo | Valore |
|-------|-------|
| Nome  | Specifica un nome significativo per il tuo volume, ad esempio, un nome che descrive la tua funzione di carico di lavoro o calcolo. Puoi immettere una combinazione di caratteri alfabetici e numerici e successivamente modificare il nome se lo desideri. |
| Profilo | Seleziona [Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) e seleziona il livello di prestazioni che desideri dall'elenco di IOPS. Se i tuoi requisiti di prestazioni non rientrano in un livello di IOPS predefinito, seleziona [Custom](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e seleziona un valore IOPS che rientra nell'intervallo di tale dimensione del volume. Fai clic sul link **storage size** per visualizzare una tabella di intervalli di dimensioni e IOPS. |
| Eliminazione automatica | Abilita questa funzione per eliminare automaticamente questo volume quando viene eliminata l'istanza del server virtuale collegata. Puoi modificare questa impostazione in un secondo momento sulla pagina dei dettagli del server virtuale. |
| IOPS | Seleziona 3, 5 o 10 IOPS/GB per un profilo a livelli |
| Dimensione | Immetti una dimensione del volume in GB.  Le dimensioni del volume possono essere comprese tra 10 GB e 2 TB. |
| Crittografia | La crittografia tramite le chiavi gestite da IBM è abilitata per impostazione predefinita su tutti i volumi. Puoi anche scegliere **Customer Managed** e utilizzare la tua chiave di crittografia.  Per prerequisiti e procedure per impostare la crittografia gestita dal cliente, vedi [Creazione dei volumi di archiviazione blocchi con la crittografia gestita dal cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Tabella 1. Valori del volume di archiviazione blocchi specificati durante il provisioning di un'istanza" caption-side="top"}

Un volume di archiviazione blocchi viene creato e collegato all'istanza del server virtuale. Nella pagina dei dettagli dell'istanza, l'elenco **Attached block storage volumes** viene aggiornato per mostrare il nuovo volume.

Un volume di archiviazione blocchi può essere collegato a soltanto un server virtuale alla volta. Nella pagina di riepilogo del volume di archiviazione blocchi, puoi visualizzare i dettagli sull'istanza del server virtuale selezionando il nome dell'istanza in **Attached instances**.

## Crea un volume di archiviazione blocchi autonomo
{: #create-standalone-vol}

Puoi creare un volume di archiviazione blocchi indipendente dal provisioning del server virtuale e collegarlo a un'istanza in un secondo momento.

1. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes** e seleziona **New volume**.
1. Immetti le informazioni nella seguente tabella per definire il tuo volume di archiviazione blocchi.
1. Quando terminato, fai clic su **Create volume**. Vieni riportato alla pagina Block storage volumes, in cui è presente un messaggio che indica che il volume è in fase di creazione. Viene visualizzato un secondo messaggio quando viene creato il volume.
1. Per visualizzare i dettagli del nuovo volume, seleziona il link **View resource** nel secondo messaggio per passare alla pagina Volume details.

| Campo | Valore |
|-------|-------|
| Nome  | Specifica un nome significativo per il tuo volume. Ad esempio, fornisci un nome che descrive la tua funzione di carico di lavoro o calcolo. Puoi immettere fino a 40 caratteri alfanumerici e successivamente modificare il nome. |
| Gruppo di risorse | Specifica un gruppo di risorse. I gruppi di risorse ti aiutano ad organizzare le tue risorse dell'account per scopi di fatturazione e controllo dell'accesso. Per informazioni sulla configurazione di un gruppo di risorse, vedi [Prassi ottimali per organizzare le risorse in un gruppo di risorse](/docs/resources?topic=resources-bp_resourcegroups#setuprgs). |
| Tag | Specifica una tag per organizzare le tue risorse. Una tag è un'etichetta che assegni a una risorsa per filtrare facilmente le risorse nel tuo elenco di risorse. Per informazioni sulle tag, vedi [Gestione delle tag](/docs/resources?topic=resources-tag). |
| Ubicazione | La zona di disponibilità nella tua regione, ereditata dal VPC (ad esempio, US South 1). |
| Dimensione | Immetti una dimensione del volume in GB.  Le dimensioni del volume possono essere comprese tra 10 GB e 2 TB. |
| IOPS | Seleziona [IOPS Tiers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) e seleziona il tile con il livello di prestazioni che desideri. |
| Personalizzato | A seconda della dimensione del volume che hai specificato, seleziona un valore IOPS all'interno dell'intervallo per tale dimensione del volume.  Fai clic sul link **storage size** per visualizzare una tabella di intervalli di dimensioni e IOPS. Per ulteriori informazioni, vedi [Profilo IOPS personalizzato](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). |
| Crittografia | La crittografia tramite le chiavi gestite da IBM è abilitata per impostazione predefinita su tutti i volumi. Per utilizzare le tue chiavi di crittografia, scegli un'opzione di crittografia gestita dal cliente. Per informazioni, vedi [Creazione dei volumi di archiviazione blocchi con la crittografia gestita dal cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).|
{: caption="Tabella 2. Valori per la definizione di un volume di archiviazione blocchi" caption-side="top"}

Preferisci creare i volumi di archiviazione blocchi utilizzando la CLI? Per informazioni, vedi [Creazione dei volumi di archiviazione blocchi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).
{: tip}

## Passi successivi
{: #next-step-creating-block-storage}

Quando aggiorni la pagina Block storage volumes, il nuovo volume viene visualizzato all'inizio dell'elenco di volumi. Se il volume è stato creato correttamente, viene mostrato uno stato Available. Per i volumi autonomi, la colonna Attachment Type è vuota (-). Il menu Action (...) alla fine di una riga della tabella fornisce un link per [collegare un volume di archiviazione blocchi a un'istanza](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Puoi continuare creando ulteriori volumi di archiviazione blocchi oppure gestendo i volumi esistenti.

* [Visualizza i dettagli su un volume di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Scollega un volume da un'istanza del server virtuale](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [Elimina un volume di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
