---

copyright:
  years: 2019
lastupdated: "2019-06-17"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

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

# Affichage des volumes de stockage par blocs à l'aide de la CLI 
{: #viewing-block-storage-cli}

Affichez des détails sur un volume de stockage par blocs ou des informations récapitulatives sur tous les volumes à partir de la CLI. 

## Avant de commencer
{: #before-viewing-block-storage-cli}

Assurez-vous d'avoir téléchargé, installé et initialisé les plug-ins CLI suivants : 

* Interface CLI d'{{site.data.keyword.cloud_notm}}
* Interface CLI de l'API d'{{site.data.keyword.cloud_notm}} Regional 

Pour plus d'informations, voir les conditions préalables requises dans [Référence CLI {{site.data.keyword.cloud_notm}} for VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Affichage des détails sur un volume de stockage par blocs à l'aide de la CLI. 
{: #viewvol-cli}

Spécifiez cette commande pour afficher des détails sur un volume. 

```bash
ibmcloud is volume VOLUME_ID [--json]
```

Exemple :

Cet exemple utilise l'ID de volume pour afficher les détails du volume. 

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Si votre volume est connecté à une instance de serveur virtuel, le nom et l'ID de la connexion et de l'instance de volume sont également affichés. 

## Affichage de tous les volumes de stockage par blocs à l'aide de la CLI 
{: #viewall-vol-cli}

Exécutez cette commande pour répertorier les informations récapitulatives sur tous les volumes : 

```bash
ibmcloud is volumes [--json]
```

Exemple :

L'exemple suivant montre tous les volumes de tous les groupes de ressources de votre zone de disponibilité.   

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

La spécification de l'ID ou du nom du groupe de ressources permet de filtrer la liste en fonction des volumes appartenant à un groupe de ressources. Lorsque vous omettez ce paramètre, tous les groupes de ressources sont définis par défaut. Vous pouvez également afficher tous les volumes d'une zone de disponibilité particulière. 

Par défaut, les 25 premiers volumes sont affichés par page. 

## Affichage des détails sur une connexion de volume à l'aide de la CLI 
{: #viewvol-attachment-cli}

Exécutez cette commande pour afficher les détails d'une connexion de volume à une instance de serveur virtuel : 

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

Spécifiez un ID d'instance et un ID de connexion de volume. Vous pouvez éventuellement exporter les détails au format JSON. 

## Affichage des détails sur toutes les connexions de volume à l'aide de la CLI 

Exécutez cette commande pour afficher toutes les connexions de volume pour une instance de serveur virtuel. 

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## Affichage des profils de volume à l'aide de la CLI 
{: #viewvol-profiles-cli}

Exécutez cette commande pour répertorier tous les profils de volume disponibles dans votre région. 

```bash
ibmcloud is volume-profiles [--json]
```

Exemple :

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## Affichage d'un profil de volume spécifique à l'aide de la CLI 
{: #viewvol-profile-cli}

Exécutez cette commande pour afficher un profil de volume spécifique dans votre région. 

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME values are 10iops-tier, 5iops-tier, general-purpose, and custom.

Exemple :

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

Vous préférez utiliser la console {{site.data.keyword.cloud}} pour afficher vos volumes de stockage par blocs ? Pour plus d'informations, voir [Affichage de volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage).
{: tip}

## Etapes suivantes
{: #next-step-viewing-block-storage-cli}

Créez d'autres volumes ou gérez vos volumes de stockage par blocs existants. 

* [Création de volumes de stockage par blocs (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [Gestion de volumes de stockage par blocs (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
