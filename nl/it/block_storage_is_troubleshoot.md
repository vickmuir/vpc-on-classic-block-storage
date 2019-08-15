---

copyright:
  years: 2019
lastupdated: "2018-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot

subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Risoluzione dei problemi con {{site.data.keyword.block_storage_is_short}}
{: #troubleshoot}

Quando crei o gestisci {{site.data.keyword.block_storage_is_short}}, potresti riscontrare dei problemi. Spesso, puoi risolvere seguendo pochi facili passi. Problemi, sintomi, cause probabili e risoluzioni sono descritti nelle seguenti sezioni.
{:shortdesc}

## Impossibile richiamare un volume in una regione specificata
{: #troubleshoot-topic-1}

Le informazioni su uno o più volumi di archiviazione blocchi potrebbero non venire richiamate per una regione specificata.
{: tsSymptoms}

Potrebbe essere dovuto a una qualsiasi delle seguenti cause:

* Mancano le informazioni e il nome del volume nell'IU o nell'output della CLI.
* Potresti anche stare tentando di accedere a un volume in un'altra regione rispetto alla tua.
* Potresti anche stare tentando di accedere a un volume di generazione 2.
{: tsCauses}

Verifica che il volume non sia stato scollegato da un'istanza del server virtuale ed eliminato. Cerca l'istanza a cui è stato collegato il volume l'ultima volta dall'elenco di tutte le istanze del server virtuale:

1. Nella console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > Compute > Virtual server instances**.

1. Seleziona un'istanza del server virtuale dall'elenco di tutti i server virtuali.

Se il volume non è collegato come previsto e non viene visualizzato nell'elenco dei volumi, probabilmente è stato eliminato.  Poiché l'eliminazione di un volume ne rimuove completamente i dati, non può essere ripristinato.  

Se utilizzi la CLI, verifica di aver immesso la sintassi corretta per la visualizzazione dei volumi. Vedi [Visualizza tutti i volumi di archiviazione blocchi dalla CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli). Verifica di aver specificato la zona o il gruppo di risorse corretti.
{: tsResolve}

## Impossibile eliminare un nome in base al nome o all'ID
{: #troubleshoot-topic-2}

Non puoi eliminare un volume di archiviazione blocchi in base al nome o all'ID.
{: tsSymptoms}

Il nome e l'ID del volume non sono accettati.
{: tsCauses}

Verifica che il nome o l'identificativo del volume siano corretti e che il volume non sia collegato a un'istanza del server virtuale. Inoltre, verifica che il volume non sia in uno stato in sospeso.
{: tsResolve}
