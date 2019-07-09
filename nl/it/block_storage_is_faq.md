---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# FAQ (frequently asked question) di Block Storage per VPC 
{: #block-storage-vpc-faq}

## Come assegno l'archiviazione per le mie istanze?
{: faq}

Quando crei un'istanza del server virtuale, puoi [creare un volume di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi) che sarà collegato a tale istanza.  Puoi anche [creare dei volumi autonomi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol) e collegarli alle tue istanze in un secondo momento.

## Quante istanze possono condividere un volume di archiviazione blocchi di cui è stato eseguito il provisioning?
{: faq}

Un volume di archiviazione blocchi può essere collegato a solo un'istanza alla volta. Le istanze non possono condividere lo stesso volume.

## Quanti volumi secondari di archiviazione blocchi (dati) possono essere collegati a un'istanza?
{: faq}

Le istanze con meno di 4 CPU virtuali possono collegare fino a 4 volumi secondari di archiviazione blocchi.

Le istanze con 4 o più CPU virtuali possono collegare fino a 12 volumi secondari di archiviazione blocchi.

## Quando eseguo il provisioning degli IOPS, tali IOPS assegnati vengono applicati all'istanza o al volume?
{: faq}

Gli IOPS vengono applicati al livello del volume. 

## Come vengono misurati gli IOPS?
{: faq}

Gli IOPS vengono misurati in base a un profilo di caricamento di blocchi da 16 KB con 50% di letture e 50% di scritture casuali. I carichi di lavoro che differiscono da questo profilo potrebbero riscontrare delle prestazioni inferiori. 

## Cosa sono i profili IOPS?
{: faq}

I profili IOPS definiscono le prestazioni di IOPS/GB per volumi di varie capacità. Esistono tre [livelli IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) predefiniti che puoi selezionare e che offrono prestazioni IOPS garantite per soddisfare i tuoi requisiti di carico di lavoro. Puoi anche definire degli [IOPS personalizzati](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e specificare un intervallo di IOPS per una dimensione del volume di tua scelta. Gli IOPS personalizzati sono una buona opzione quando disponi di requisiti di prestazioni ben definiti che non rientrano in un intervallo IOPS predefinito.

## Qual è il numero massimo di IOPS che posso attendermi per i miei volumi di dati?
{: faq}

Il numero massimo di IOPS per i volumi di dati varia in base alla dimensione del volume e al profilo di livello IOPS che hai selezionato. Ad esempio, il numero massimo di IOPS per un volume di ambito generale fino a 1 TB è di 3.000 IOPS. Per informazioni, vedi [Profili IOPS a livelli](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). Se scegli un [Profilo IOPS personalizzato](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom), definisci anche un intervallo minimo e massimo per una specifica dimensione del volume.

## Cosa succede se uso una dimensione blocco più piccola quando misuro le prestazioni? 
{: faq}

Quando si utilizzano delle dimensioni blocco più piccole, è comunque possibile ottenere l'IOPS massimo; tuttavia, la velocità effettiva sarà inferiore. Ad esempio, un volume con 6000 IOPS avrà la seguente velocità effettiva alle varie dimensioni blocco: 

* 16 KB * 6000 IOPS == ~93.75 MB/sec
* 8 KB * 6000 IOPS == ~46.88 MB/sec
* 4 KB * 6000 IOPS == ~23.44 MB/sec

## Mi saranno addebitati dei costi per l'utilizzo e ci sono dei limiti di quota?
{: faq}

Per ulteriori informazioni su cosa ti viene fatturato, vedi [Prezzi per Block Storage per VPC](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing). Si applicano alcuni limiti.
Per ulteriori informazioni sulle quote e sui limiti per il tuo {{site.data.keyword.cloud}} Virtual Private Cloud e sulle risorse disponibili in esso, vedi [Quote](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas).

## Dopo aver creato un volume, posso incrementarne la capacità in un secondo momento?
{: faq}

No, non puoi incrementare la capacità di un volume.  Ti consigliamo di stimare una capacità sufficiente per la crescita prevista prima di eseguire il provisioning di un volume di archiviazione blocchi.

## Occorre preriscaldare il volume per ottenere la velocità effettiva prevista?
{: faq}

Non devi preriscaldare un volume. Puoi vedere la velocità effettiva specificata immediatamente dopo il provisioning del volume.

## Posso creare dei volumi crittografati?
{: faq}

Tutti i volumi di archiviazione blocchi sono crittografati, tramite la crittografia gestita da IBM (valore predefinito) oppure tramite il servizio Key Protect utilizzando le tue chiavi di crittografia.  Per informazioni, vedi [Creazione dei volumi di archiviazione blocchi con la crittografia gestita dal cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

## Come posso conoscere qual è il tipo di crittografia di un volume?
{: faq}

Dall'IU, quando visualizzi il tuo elenco di tutti i volumi di archiviazione blocchi, la colonna Encryption indica se la crittografia è gestita dal provider o dal cliente.

Per mostrare le proprietà di un volume dalla CLI, immetti:

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## Quanto sono sicuri i miei dati?
{: faq}

Tutti i volumi di archiviazione blocchi sono crittografati quando non attivi dalla crittografia gestita da IBM o tramite le tue chiavi di crittografia. Le chiavi gestite da IBM vengono generate e archiviate in modo sicuro in un archivio di archiviazione blocchi supportato da Consul e poi conservato dal sistema. Le chiavi gestite dal cliente vengono gestite in modo sicuro tramite il servizio IBM Key Protect.

## Come mi devo comportare riguardo i backup dei dati per il ripristino di emergenza?
{: faq}

Block Storage per VPC protegge i tuoi dati tramite zone di errori ridondanti nella tua regione. Ti consigliamo inoltre di eseguire il backup dei tuoi dati in modo indipendente. Puoi anche considerare di utilizzare [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started), che fornisce delle funzioni di ripristino di emergenza come le istantanee, la replica e la clonazione del volume.

## Di quanti volumi posso eseguire il provisioning?
{: faq}

Puoi eseguire il provisioning di un massimo di 1.000 volumi di archiviazione blocchi per regione.

## Quale strategia dovrei utilizzare per gestire i miei volumi?
{: faq}

Determina la capacità di cui hai bisogno in base alla crescita prevista. La dimensione del volume non può essere espansa dopo il provisioning. Tuttavia, puoi creare dei nuovi volumi se necessario. Inoltre, se hai dei requisiti di prestazioni ben definiti, potresti considerare di scegliere degli [IOPS personalizzati](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) che forniscono un intervallo specifico di IOPS per dimensione del volume.

## Come viene creato il disco di avvio di un'istanza del server virtuale e come è correlato al file dell'immagine?
{: faq}

Il disco di avvio, noto anche come un volume di avvio, viene creato quando esegui il provisioning di un'istanza del server virtuale. Il disco di avvio di un'istanza è un'immagine clonata dell'immagine della macchina virtuale. Il volume di avvio viene eliminato quando elimini l'istanza a cui è collegato.

## I firewall o i gruppi di sicurezza influenzano le prestazioni?
{: faq}

Come procedura consigliata, ti consigliamo di eseguire il traffico di archiviazione su una VLAN che ignora il firewall. L'esecuzione del traffico di archiviazione tramite i firewall software aumenta la latenza e ha un impatto negativo sulle prestazioni dell'archiviazione.

## Quando posso eliminare un volume di dati di archiviazione blocchi?
{: faq}

Puoi eliminare un volume di dati di archiviazione blocchi solo quando non è collegato a un'istanza del server virtuale. [Scollega il volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach) prima di eliminarlo. I volumi di avvio vengono scollegati ed eliminati quando viene eliminata l'istanza.

## Cosa succede ai miei dati quando elimino un volume di dati di archiviazione blocchi?
{: faq}

Quando elimini un volume di dati di archiviazione blocchi, tutti i puntatori ai dati su tale volume vengono rimossi e i dati diventano completamente inaccessibili. Se riesegui successivamente il provisioning dell'archiviazione fisica su un altro account, viene assegnata una nuova serie di puntatori. Non c'è modo per questo nuovo account di accedere ai dati che potevano trovarsi sull'archiviazione fisica; la nuova serie di puntatori mostra tutti 0. Quando vengono scritti dei nuovi dati sul volume, tutti i dati inaccessibili vengono sovrascritti.

## Quale latenza di prestazioni possono attendermi dalla mia archiviazione blocchi?
{: faq}

La latenza di destinazione all'interno dell'archiviazione è meno di 1 millisecondo. L'archiviazione blocchi viene connessa alle istanze di calcolo su una rete condivisa, in modo che la latenza di prestazioni esatta dipenderà dal traffico di rete all'interno di un intervallo di tempo specificato.

## Posso configurare l'archiviazione condivisa in un cluster multizona?
{: faq}

In IBM Cloud, le opzioni di archiviazione vengono localizzate su una zona di disponibilità. Non ti consigliamo di gestire l'archiviazione condivisa in più zone.

Invece, utilizza un'opzione del servizio classico di dati IBM Cloud come ad esempio {{site.data.keyword.cos_full}} o {{site.data.keyword.cloudantfull}} se devi condividere i tuoi dati tra più zone e regioni.

## Ho dei volumi sull'infrastruttura classica. Posso portarli nel VPC?
{: faq}

No. Il VPC fornisce l'accesso a nuove zone di disponibilità in regioni multizona. Le risorse di calcolo, rete e archiviazione vengono specificatamente progettate per funzionare nel VPC.
