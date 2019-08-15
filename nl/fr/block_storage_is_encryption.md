---

Copyright:
  years: 2019
lastupdated: "2019-07-23"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance, customer-managed encryption

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Création de volumes de stockage par blocs avec un chiffrement géré par le client
{: #block-storage-encryption}

Par défaut, les volumes de démarrage et de données {{site.data.keyword.block_storage_is_short}} sont chiffrés à l'aide du chiffrement géré par IBM. Vous pouvez également créer des volumes chiffrés gérés par le client à l'aide d'un service de gestion de clé pris en charge pour créer ou importer votre clé racine client. Le chiffrement géré par le client est une option pour les volumes d'amorçage et de données créés lors de la mise à disposition de l'instance.  Vous pouvez également spécifier un chiffrement géré par le client lorsque vous créez un volume de données autonome.
{:shortdesc}

## Services de gestion de clés pour les volumes de stockage par blocs
{: #key-mgt-services-for-storage}

Deux services de gestion de clé sont disponibles, {{site.data.keyword.keymanagementserviceshort}} et {{site.data.keyword.hscrypto}} (disponibles dans certaines [régions](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)). Les centres de données {{site.data.keyword.cloud_notm}} fournissent un module de sécurité matérielle (HSM) dédié pour protéger vos clés. Le tableau suivant fournit des informations sur chaque service.

| Service de gestion de clés | Certification de chiffrement HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conformité à FIPS 140-2 *Level 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conformité à FIPS 140-2 *Level 4* |
{: caption="Tableau 1. Services de gestion des clés pour {{site.data.keyword.block_storage_is_short}}" caption-side="top"}

## Prérequis
{: #custom-managed-vol-prereqs}

Pour créer des volumes de stockage par blocs avec un chiffrement géré par le client, vous devez d'abord mettre à disposition un service de gestion de clés et créer ou importer votre clé racine client.
Vous devez également autoriser l'accès entre Cloud Block Storage et le service de gestion de clés. Une fois ces conditions préalables remplies, vous pouvez commencer à créer des volumes de stockage par blocs qui utilisent le chiffrement géré par le client.

Les étapes suivantes sont spécifiques à {{site.data.keyword.keymanagementserviceshort}}, mais le flux général s'applique également à {{site.data.keyword.hscrypto}}.  Si vous utilisez {{site.data.keyword.hscrypto}}, reportez-vous aux [informations relatives à {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) pour obtenir les instructions correspondantes.
{:note}

1. Mettez à disposition le service [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision).

   La mise à disposition d'une nouvelle instance de service {{site.data.keyword.keymanagementserviceshort}} garantit qu'elle inclut les dernières mises à jour requises pour le chiffrement géré par le client des volumes de stockage par blocs. Les instances {{site.data.keyword.keymanagementserviceshort}} créées en 2019 incluent l'extension requise pour prendre en charge le chiffrement géré par le client.
   {: tip}

2. [Créez](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) ou
[importez](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) une clé racine client (CRK) dans {{site.data.keyword.keymanagementservicelong_notm}}.
3. A partir d'IBM {{site.data.keyword.iamshort}} (IAM), [autorisez l'accès](/docs/iam?topic=iam-serviceauth#serviceauth) entre **Cloud Block Storage** (service source) et **{{site.data.keyword.keymanagementserviceshort}}** (service cible).

## Création de volumes de données chiffrés gérés par le client à l'aide de l'interface utilisateur
{: #data-vol-encryption-ui}

Vous pouvez spécifier un chiffrement géré par le client lorsque vous créez un nouveau volume de stockage par blocs lors de la mise à disposition de l'instance ou en tant que volume autonome.

Pour créer un volume chiffré lorsque vous créez une instance de serveur virtuel, voir [Création d'instances de serveur virtuel avec chiffrement géré par le client](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok).

Pour spécifier le chiffrement géré par le client lors de la création d'un volume autonome, procédez comme suit :

1. Dans la console {{site.data.keyword.cloud_notm}}, accédez à **l'icône Menu ![Icône Menu](../../icons/icon_hamburger.svg) > Infrastructure VPC > Stockage > Volumes de stockage par blocs**.
La liste de tous les volumes de stockage par blocs s'affiche.
1. Sélectionnez **Nouveau volume**.
1. Sur la page **Nouveau volume de stockage par blocs**, mettez à jour les zones de la section **Chiffrement**. Pour plus d'informations, reportez-vous au tableau ci-dessous. Une fois vos modifications terminées, cliquez sur **Créer un volume**.

| Zone | Valeur |
| ----- | ----- |
| Chiffrement | _Géré par le fournisseur_ est le mode de chiffrement par défaut. Pour utiliser le chiffrement géré par le client, sélectionnez un service de gestion de clés ({{site.data.keyword.keymanagementserviceshort}} ou {{site.data.keyword.hscrypto}}). L'instance de service de gestion de clés doit inclure la clé racine du client que vous souhaitez utiliser pour le chiffrement géré par le client. |
| Instance de service de chiffrement | Si plusieurs instances de service de gestion de clés sont mises à disposition dans votre compte, sélectionnez celle qui inclut la clé racine du client que vous souhaitez utiliser pour le chiffrement géré par le client. |
| Nom de clé | Sélectionnez la clé de chiffrement de données dans l'instance {{site.data.keyword.keymanagementserviceshort}} que vous souhaitez utiliser pour chiffrer le volume. |
| ID clé | Affiche l'ID clé associé à la clé de chiffrement de données que vous avez sélectionnée. |
{: caption="Tableau 1. Valeurs pour le chiffrement géré par le client" caption-side="top"}

## Création de volumes de données chiffrés gérés par le client à l'aide de la CLI
{: #data-vol-encryption-cli}

Pour créer un volume de stockage par blocs avec un chiffrement géré par le client à l'aide de la CLI, indiquez la commande `ibmcloud is volume-create` avec le paramètre `--encryption-key` :

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Le paramètre `--encryption-key` prend le CRN de la clé racine. Obtenez le numéro CRN de la clé racine dans votre instance de service de gestion de clés. Pour plus d'informations, voir la [documentation de l'instance de serveur virtuel sur le chiffrement géré par le client](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli). Pour plus d'informations sur la création de volumes de stockage par blocs à l'aide de la CLI, voir [Création de volumes de stockage par blocs à l'aide de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

L'exemple suivant montre un nouveau volume créé avec un chiffrement géré par le client.

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

Vous pouvez également créer des volumes avec un chiffrement géré par le client lors de la mise à disposition de l'instance.  Pour plus d'informations, voir [Utilisation de l'interface CLI pour mettre à disposition des instances et des volumes avec un chiffrement géré par le client](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli).

## Modification des volumes d'amorçage pour utiliser le chiffrement géré par le client à l'aide de l'interface utilisateur

Lorsque vous créez une instance à partir de l'interface utilisateur, vous pouvez spécifier le chiffrement géré par le client en modifiant les propriétés du volume d'amorçage. Pour plus d'informations, voir [Mise à disposition d'instances de serveur virtuel avec des volumes utilisant le chiffrement géré par le client](docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-ui).
