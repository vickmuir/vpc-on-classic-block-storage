---

Copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Creazione dei volumi di archiviazione blocchi con la crittografia gestita dal cliente 
{: #block-storage-encryption}

Per impostazione predefinita, i volumi di dati e avvio {{site.data.keyword.block_storage_is_short}} sono crittografati con la crittografia gestita da IBM. Puoi anche creare dei volumi crittografati gestiti dal cliente utilizzando un servizio di gestione delle chiavi supportato per creare o importare la chiave root del cliente. La crittografia gestita dal cliente è un'opzione per i volumi di dati e avvio creati durante il provisioning dell'istanza.  Puoi anche specificare la crittografia gestita dal cliente quando crei un volume di dati autonomo.  

## Servizi di gestione delle chiavi per i volumi di archiviazione blocchi
{: #key-mgt-services-for-storage}

Sono disponibili due servizi di gestione delle chiavi, {{site.data.keyword.keymanagementserviceshort}} e {{site.data.keyword.hscrypto}} (disponibile in alcune regioni [](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)). I data center di {{site.data.keyword.cloud_notm}} forniscono un HSM (hardware security module) dedicato per proteggere le tue chiavi. La seguente tabella fornisce le informazioni su ogni servizio.

| Servizio di gestione delle chiavi | Certificazione di crittografia HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conforme a FIPS 140-2 *Level 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conforme a FIPS 140-2 *Level 4* |

## Prerequisiti
{: #custom-managed-vol-prereqs}

Per creare dei volumi di archiviazione blocchi con la crittografia gestita dal cliente, devi prima eseguire il provisioning di un servizio di gestione delle chiavi e creare o importare la tua chiave root del cliente.
Devi anche autorizzare l'accesso tra Cloud Block Storage e il servizio di gestione delle chiavi. Quando hai completato questi prerequisiti, puoi iniziare a creare dei volumi di archiviazione blocchi che utilizzano la crittografia gestita dal cliente.

La seguente procedura è specifica per {{site.data.keyword.keymanagementserviceshort}}, ma il flusso generale si applica anche a {{site.data.keyword.hscrypto}}.  Se stai utilizzando {{site.data.keyword.hscrypto}}, vedi le [informazioni su {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) per delle istruzioni corrispondenti.
{:note}

1. Esegui il provisioning del servizio [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision).

   Eseguire il provisioning di una nuova istanza del servizio {{site.data.keyword.keymanagementserviceshort}} ti garantisce che essa includa gli aggiornamenti più recenti necessari per la crittografia gestita dal cliente dei volumi di archiviazione blocchi. Le istanze di {{site.data.keyword.keymanagementserviceshort}} create nel 2019 includono l'estensione necessaria per supportate la crittografia gestita dal cliente.
   {: tip}

2. [Crea](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) o
[importa](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) una chiave root del cliente (CRK) in
{{site.data.keyword.keymanagementservicelong_notm}}.
3. Da IBM {{site.data.keyword.iamshort}} (IAM), [autorizza l'accesso](/docs/iam?topic=iam-serviceauth#serviceauth) tra **Cloud Block Storage** (servizio di origine) e **{{site.data.keyword.keymanagementserviceshort}}** (servizio di destinazione).

## Creazione dei volumi di dati crittografati e gestiti dal cliente utilizzando l'IU
{: #data-vol-encryption-ui}

Puoi specificare la crittografia gestita dal cliente quando crei un nuovo volume di archiviazione blocchi durante il provisioning dell'istanza o come un volume autonomo. 

Per creare un volume crittografato quando crei un'istanza del server virtuale, vedi [Creazione delle istanze del server virtuale con la crittografia gestita dal cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok).

Per specificare la crittografia gestita dal cliente durante la creazione di un volume autonomo, segui questa procedura:

1. Nella console {{site.data.keyword.cloud_notm}}, passa a **Menu icon ![Icona menu](../../icons/icon_hamburger.svg) > VPC Infrastructure > Storage > Block storage volumes**.
Viene visualizzato un elenco di tutti i volumi di archiviazione blocchi.
1. Seleziona **New volume**. Nella pagina New block storage volume, aggiorna i campi nella sezione Encryption.
1. Nella pagina **New block storage volume**, aggiorna i campi nella sezione **Encryption**. Per ulteriori informazioni, vedi la seguente tabella. Quando hai terminato di apportate modifiche, fai clic su **Create Volume**.

| Campo | Valore |
| ----- | ----- |
| Crittografia |_Provider managed_ è la modalità di crittografia predefinita. Per utilizzare la crittografia gestita dal cliente, seleziona un servizio di gestione delle chiavi ({{site.data.keyword.keymanagementserviceshort}} o {{site.data.keyword.hscrypto}}). L'istanza del servizio di gestione delle chiavi dovrebbe includere la chiave root del cliente che vuoi utilizzare per la crittografia gestita dal cliente. |
| Istanza del servizio di crittografia |Se disponi di più istanze del servizio di gestione delle chiavi di cui è stato eseguito il provisioning nel tuo account, seleziona quella che include la chiave root del cliente che vuoi utilizzare per la crittografia gestita dal cliente. |
|Nome della chiave| Seleziona la chiave di crittografia dei dati all'interno dell'istanza di {{site.data.keyword.keymanagementserviceshort}} che vuoi utilizzare per crittografare il volume. |
|ID chiave| Visualizza l'ID chiave associato alla chiave di crittografia dei dati che hai selezionato. |
{: caption="Tabella 1. Valori per la crittografia gestita dal cliente" caption-side="top"}

## Creazione dei volumi di dati crittografati e gestiti dal cliente utilizzando la CLI 
{: #data-vol-encryption-cli}

Per creare un volume di archiviazione blocchi con la crittografia gestita dal cliente utilizzando la CLI, specifica il parametro `ibmcloud is volume-create` con il parametro `--encryption-key`.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Il parametro `--encryption-key` prende il CRN della chiave root. Ottieni il CRN della chiave root nella tua istanza del servizio di gestione delle chiavi. Per informazioni, vedi la [documentazione dell'istanza del server virtuale sulla crittografia gestita dal cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli). Per informazioni sulla creazione di volumi di archiviazione blocchi utilizzando la CLI, vedi [Creazione dei volumi di archiviazione blocchi utilizzando la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

Il seguente esempio mostra un nuovo volume creato con la crittografia gestita dal cliente.

```bash
$ ibmcloud is volume-create demo_volume custom us-south-1 --iops 1000 --encryption-key abccorp-kp-vpc-2 5437644a-c4b1-447f-9646-b1a2a4df61382
Creating volume demovolume in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          crn:v1:bluemix:public:kms:us-south:a/8d65fb1cf5e99e86dd7229ddef9e5b7b:b1abf7c5-381d-4f34-836e-5db7193250bc:key:fd57250e-908c-4785-a8a5-1f53176bcd2f
Encryption                              customer_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Puoi anche creare i volumi con la crittografia gestita dal cliente durante il provisioning dell'istanza.  Per informazioni, vedi [Utilizzo della CLI per eseguire il provisioning di istanze e volumi con la crittografia gestita dal cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli).

## Modifica dei volumi di avvio in modo che utilizzino la crittografia gestita dal cliente tramite l'IU

Quando crei un'istanza dall'IU, puoi specificare la crittografia gestita dal cliente modificando le proprietà del volume di avvio. Per informazioni, vedi [Provisioning delle istanze del server virtuale con volumi che utilizzano la crittografia gestita dal cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#provision-byok-ui).
