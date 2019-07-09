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

# Gestione dei volumi di archiviazione blocchi utilizzando l'IU 
{: #managing-block-storage}

## Scollega un volume di archiviazione blocchi da un'istanza del server virtuale 
{: #detach}

Puoi scollegare un volume di archiviazione blocchi che è al momento collegato a un'istanza del server virtuale.  Lo scollegamento libera il volume in modo che possa essere utilizzato da un'altra istanza.

Per scollegare un volume:

1. Passa all'elenco di tutti i volumi di archiviazione blocchi. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), vai a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Individua il volume e fai poi clic sui puntini di sospensione (...) alla fine della riga della tabella. Viene visualizzato un menu contestuale.
1. Dal menu, fai clic su **Detach from instance**.
1. Conferma facendo clic su **Detach instance** nella finestra a comparsa.

In alternativa, puoi fare clic su un singolo volume nell'elenco di tutti i volumi di archiviazione blocchi e passare alla pagina **Volume Details** di tale volume. In **Attached instances**, fai clic sul segno meno accanto all'istanza del server virtuale per scollegare il volume da tale istanza.

## Trasferisci un volume di archiviazione blocchi da un'istanza del server virtuale a un'altra.
{: #transfer}

Per trasferire un volume di archiviazione blocchi a un'altra istanza del server virtuale:

1. [Scollega il volume dalla sua istanza del server virtuale](#detach).
1. Passa all'istanza del server virtuale a cui vuoi trasferire il volume. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), vai a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Compute > Virtual server instances for VPC**.
1. Seleziona un server virtuale dall'elenco.
1. In Attached Storage volumes, fai clic sul segno più per aggiungere un volume. Vengono visualizzati tutti i volumi di archiviazione blocchi.
1. Dall'elenco dei volumi, seleziona quello che hai precedentemente scollegato.

## Collega un volume di archiviazione blocchi precedentemente collegato
{: #reattach}

I volumi di archiviazione blocchi vengono collegati per impostazione predefinita quando crei una nuova istanza del server virtuale.  Quando scolleghi un volume da un'istanza, rimane come un volume scollegato e viene visualizzato nell'elenco di [tutti i volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). Puoi collegarlo a un'altra immagine dall'elenco di volumi di archiviazione blocchi.

1. Passa all'elenco di tutti i volumi di archiviazione blocchi. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Individua il volume e fai poi clic sui puntini di sospensione (...) alla fine della riga della tabella. Viene visualizzato un menu contestuale.
1. Dal menu, fai clic su **Attach to instance**.
1. Seleziona un'istanza del server virtuale.
1. Conferma la tua selezione.

## Ridenomina un volume di archiviazione blocchi
{: #rename}

Puoi modificare il nome di un volume esistente per renderlo più significativo.

1. Passa all'elenco di tutti i volumi di archiviazione blocchi. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), vai a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Individua il volume e fai poi clic sul nome del volume per andare alla pagina Volume Details.
1. Fai clic sull'icona matita dopo il nome del volume e modificalo.
1. Conferma la tua modifica.

## Elimina un volume di archiviazione blocchi
{: #delete}

L'eliminazione di un volume di archiviazione blocchi ne rimuove completamente i dati. Il volume non può essere ripristinato.

Non puoi eliminare un volume di archiviazione blocchi attivo. Per eliminare un volume, devi prima [scollegarlo](#detach) dal server virtuale e poi seguire questa procedura:

1. Passa all'elenco di tutti i volumi di archiviazione blocchi. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), vai a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Storage > Block storage volumes for VPC**.
1. Individua il volume che vuoi eliminare e fai poi clic sui puntini di sospensione alla fine della riga della tabella. Viene visualizzato un menu contestuale.
1. Dal menu, fai clic su **Delete**.
1. Conferma l'eliminazione. 

## Eliminazione automatica di volumi di dati di archiviazione blocchi
{: #auto-delete}

Utilizzando la funzione Auto Delete, puoi specificare che un volume di dati di archiviazione blocchi venga automaticamente eliminato quando elimini un'istanza a cui è collegato. Questa funzione non si applica ai volumi di avvio ed è disabilitata per impostazione predefinita.

Per abilitare Auto Delete per un volume di archiviazione blocchi esistente collegato a un'istanza, segui questa procedura:

1. Individua l'istanza del server virtuale a cui è collegato il volume. Nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} per il VPC (Virtual Private Cloud), passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Compute > Virtual server instances for VPC**.
1. In **Attached block storage volumes**, seleziona un volume.
1. Nel menu a comparsa, fai clic sul pulsante Auto Delete per l'abilitazione.
1. Conferma la tua selezione.

In alternativa, inizia selezionando un volume dall'elenco di volumi di archiviazione blocchi (**Storage > Block storage volumes for VPC**).

Per abilitare Auto Delete su un nuovo volume quando crei un'istanza, vedi [Crea e collega un volume di archiviazione blocchi quando crei una nuova istanza](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi).

## Assegna l'accesso a un volume di archiviazione blocchi
{: #assign-volume-access}

Con i privilegi da amministratore, puoi assegnare l'accesso utente al livello del volume al servizio {{site.data.keyword.block_storage_is_short}}. La seguente tabella mostra le informazioni che devi fornire nell'[IU di Identity and Access Management (IAM)](/docs/iam?topic=iam-account_setup#assigning-access).

|Campo IAM |Azione |
|--------|-------------|
| Servizi  | Seleziona **Infrastructure Services** |
|Tipo di risorsa| Seleziona **Block Storage for VPC** |
|ID volume | Immetti l'[ID volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) per assegnare l'accesso a uno specifico volume |
|Seleziona ruoli| Assegna i ruoli di accesso alla piattaforma, normalmente, Operatore |

Per ulteriori informazioni, vedi le [procedure consigliate per l'assegnazione dell'accesso](/docs/iam?topic=iam-account_setup#account_setup). Per il processo IAM completo, che include l'invito di utenti nel tuo account e l'assegnazione dell'acceso Cloud IAM, vedi l'[esercitazione introduttiva IAM](/docs/iam?topic=iam-getstarted#getstarted).

## Stato del volume di archiviazione blocchi
{: #status}

La seguente tabella mostra gli stati che potresti visualizzare durante la creazione, la visualizzazione o la gestione dei tuoi volumi di archiviazione blocchi.

| Stato |Significato|
|--------|-------------|
|Disponibile| Un volume è stato richiamato correttamente |
| | Un volume è disponibile e può essere collegato a un'istanza |
| | Un volume collegato è disponibile per i dati
| | Un volume di avvio è disponibile |
|Non riuscito| Creazione di un volume non riuscita |
| | Impossibile richiamare tutti i volumi in una regione |
| | Impossibile trovare un volume con l'ID volume specificato |
| | Impossibile eliminare un volume |
|In sospeso| Un volume è in fase di creazione |
| | Un volume è in fase di collegamento a un'istanza |
| Eliminazione in sospeso | Un volume è in fase di eliminazione |

Preferisci gestire i volumi di archiviazione blocchi utilizzando la CLI? Per informazioni, vedi [Gestione dei volumi di archiviazione blocchi (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli).
{: tip}

## Passi successivi
{: #next-step-managing-block-storage}

Puoi [creare ulteriori volumi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

Per problemi con i volumi di archiviazione blocchi esistenti, potresti essere in grado di risolvere i problemi da solo. Per ulteriori informazioni, vedi [Risoluzione dei problemi per l'archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
