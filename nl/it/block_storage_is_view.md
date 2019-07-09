---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

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

# Visualizzazione dei dettagli del volume di archiviazione blocchi
{: #viewing-block-storage}

Visualizza i dettagli su un volume di archiviazione blocchi o le informazioni di riepilogo su tutti i volumi. 

## Visualizza le informazioni su tutti i volumi di archiviazione blocchi
{: #viewvols}

Passa all'elenco dei volumi di archiviazione blocchi. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), vai a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.

Per impostazione predefinita, i volumi di archiviazione blocchi sono visualizzati per tutti i gruppi di risorse nella tua regione.  Nell'elenco di tutti i **volumi di archiviazioni blocchi**, visualizzerai le seguenti informazioni.

| Campo |Descrizione|
|-------|-------------|
| Stato | Lo stato del volume, con funzioni come il filtro predefinito per tutte le righe. Per informazioni sugli stati dei volumi, vedi [Stati del volume di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status). |
| Nome | Fai clic sul nome del volume per visualizzarne i relativi dettagli. |
| Gruppo di risorse |  Il gruppo di risorse definito quando configuri il tuo VPC. I gruppi di risorse gestiscono l'accesso alle risorse ma non influenzano la fatturazione o il monitoraggio.|
| Ubicazione | La zona di disponibilità nella tua regione, ereditata dal VPC (ad esempio, US South 1). |
| Dimensione | La dimensione del volume che hai specificato, in GB. |
| Numero massimo di IOPS | Il numero massimo di IOPS disponibili, definito dal livello IOPS di ambito generico o dal valore di IOPS personalizzato che hai specificato. |
| Tipo di collegamento | Dati, per un volume secondario collegato a un'istanza, avvio quando collegato come un volume di avvio o vuoto per un volume non collegato. |
| Crittografia | Gestita dal provider o [gestita dal cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
| Azioni (...) | Fai clic sui puntini di sospensione per visualizzare un menu di azioni specifiche per il contesto che puoi effettuare.  Ad esempio, un volume disponibile e scollegato avrebbe delle opzioni di menu per il collegamento a un'istanza o l'eliminazione del volume. |
{: caption="Tabella 1. Dettagli su tutti i volumi" caption-side="top"}

Per impostazione predefinita, vengono mostrati 10 volumi nell'elenco di tutti i volumi di archiviazione blocchi.  Modifica questo valore predefinito facendo clic sulla freccia a discesa e aumenta l'elenco a 20 o 50 volumi.  Utilizza le frecce nell'angolo inferiore destro per andare avanti o indietro con le pagine.

## Visualizza i dettagli su un volume di archiviazione blocchi 
{: #view-vol-details}

Per visualizzare i dettagli su un volume di archiviazione blocchi, passa all'elenco di tutti i volumi di archiviazione blocchi e selezionane uno.  Per un solo volume, visualizzerai le seguenti informazioni.

| Campo |Descrizione|
|-------|-------------|
| Nome  | Il nome del volume che hai specificato quando hai creato il volume. Fai clic sull'icona matita per modificare il nome del volume. |
|Gruppo di risorse|  Il gruppo di risorse definito quando configuri il tuo VPC. I gruppi di risorse gestiscono l'accesso alle risorse ma non influenzano la fatturazione o il monitoraggio.|
| Tipo di collegamento | Dati, per un volume secondario collegato a un'istanza, avvio quando collegato come un volume di avvio o vuoto per un volume non collegato. |
| ID | L'ID volume generato dal sistema. |
| Creato| La data generata dal sistema in cui è stato creato il volume. |
| Ubicazione | La zona di disponibilità nella tua regione. |
| Dimensione | La dimensione del volume che hai specificato. |
| Profilo | Il profilo livello IOPS o IOPS personalizzato. |
| Numero massimo di IOPS | Il valore numero massimo di IOPS di un livello IOPS predefinito o il valore che hai specificato per gli IOPS personalizzati. |
|Velocità effettiva| Le prestazioni che può raggiungere un disco, misurate in gigabit/secondo (Gbps).  Basata sul tuo profilo del volume, la velocità effettiva viene calcolata come la quantità di IOPS * la dimensione blocco di 16K. |
| Crittografia | Gestita dal provider o dal cliente. |
{: caption="Tabella 1. Dettagli volume" caption-side="top"}

I volumi collegati a un'istanza del server virtuale vengono visualizzati in **Attached instances** nella pagina **Volume details**.  Puoi anche [collegare un volume a un'istanza](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Per quanto riguarda un volume collegato a un'istanza, puoi anche passare alle informazioni sull'istanza e poi ritornare a un elenco di tutti i volumi Block Storage.

## Visualizza i dettagli del volume di archiviazione blocchi nei dettagli dell'istanza

Puoi visualizzare le informazioni su un volume di archiviazione blocchi collegato dalla pagina **Virtual server instance details**:

1. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, vai a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Compute > Virtual server instances for VPC** e seleziona un'istanza.
1. In **Attached block storage volumes**, fai clic sul nome di un volume per andare alla relativa pagina dei dettagli.

Preferisci visualizzare i volumi di archiviazione blocchi utilizzando la CLI? Per informazioni, vedi [Visualizzazione dei volumi di archiviazione blocchi (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli).
{: tip}

## Passi successivi
{: #next-step-viewing-block-storage}

Crea ulteriori volumi o gestisci i tuoi volumi di archiviazione blocchi esistenti.

* [Creazione dei volumi di archiviazione blocchi nella console IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gestione dei volumi di archiviazione blocchi utilizzando l'IU](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
