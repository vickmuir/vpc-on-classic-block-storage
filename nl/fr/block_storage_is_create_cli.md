---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM CLoud, VPC, virtual private cloud, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Création de volumes de stockage par blocs à l'aide de la CLI
{: #creating-block-storage-cli}

Vous pouvez créer des volumes {{site.data.keyword.block_storage_is_short}} à l'aide de l'interface de ligne de commande (CLI).
{:shortdesc}

## Avant de commencer
{: #before-creating-block-storage-cli}

1. Assurez-vous d'avoir téléchargé, installé et initialisé les plug-ins CLI suivants :
    * Interface CLI d'{{site.data.keyword.cloud_notm}}
    * Plug-in infrastructure-service

   Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Lorsque vous installez le plug-in vpc-infrastructure pour la première fois, vous devez définir la génération cible sur gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assurez-vous que vous avez déjà [créé une instance {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Création d'un volume de stockage par blocs à l'aide de la CLI
{: #create-vol-cli}

Exécutez la commande suivante.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Exemple :

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

La capacité, indiquée en mégaoctets, peut aller de 10 à 2 000 Go.  Les valeurs d'IOPS peuvent aller de 1 000 à 20 000 IOPS, en fonction de la taille du volume. Si vous ne spécifiez pas de valeur IOPS, la configuration valide par profil de volume est utilisée par défaut. Pour plus d'informations, voir le tableau [Plages d'IOPS en fonction de la taille de volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).

L'ID de volume dans l'exemple ci-dessus est utilisé lors de la connexion d'un volume de stockage par blocs à une instance de serveur virtuel, de l'affichage des détails du volume de stockage par blocs et de la suppression de volumes.

Vous préférez créer des volumes de stockage par blocs à l'aide de la console {{site.data.keyword.cloud}} ? Pour plus d'informations, voir [Création de volumes de stockage par blocs ](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
{: tip}

## Etapes suivantes
{: #next-step-creating-block-storage-cli}

[Connexion d'un volume de stockage par blocs à l'aide de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
