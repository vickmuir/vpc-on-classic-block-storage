---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Gestion de volumes de stockage par blocs à l'aide de la CLI
{: #managing-block-storage-cli}

Gérez {{site.data.keyword.block_storage_is_short}} à partir de l'interface de ligne de commande (CLI). Mettez à jour un nom de volume ou une pièce jointe de volume, détachez un volume ou supprimez un volume.
{:shortdesc}

## Avant de commencer
{: #before-managing-block-storage-cli}

1. Assurez-vous d'avoir téléchargé, installé et initialisé les plug-ins CLI suivants :
    * Interface CLI d'{{site.data.keyword.cloud_notm}}
    * Plug-in infrastructure-service

   Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Lorsque vous installez le plug-in vpc-infrastructure pour la première fois, vous devez définir la génération cible sur gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assurez-vous que vous avez déjà [créé une instance {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Mise à jour le nom d'un volume
{: #update-vol-name}

Pour modifier un nom de volume, spécifiez le nom du volume ou son ID, puis indiquez le nouveau nom.

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

Exemple :

```bash
$ ibmcloud is volume-update 933c8781-f7f5-4a8f-8a2d-3bfc711788ee --name demo-volume-update
Updating volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount 01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo-volume-update
Capacity                                100
IOPS                                    1000
Profile                                 5iops-tier
Encryption                              -
Encryption                              provider managed
Status                                  available
Created                                 2019-05-20 10:09:28
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Zone                                    us-south-2
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Volume Attachment Instance Reference    none
```
{: screen}

## Mise à jour d'une connexion de volume à l'aide de la CLI
{: #update-vol-name-cli}

Vous pouvez mettre à jour le nom de la connexion du volume et modifier le paramètre de suppression automatique par défaut à l'aide de la commande `instance-volume-attachment-update`.

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

Utilisez le paramètre `--name` et spécifiez un nouveau nom pour la connexion au volume.

Spécifiez `--auto-delete true` pour supprimer automatiquement le volume lorsque vous supprimez l'instance à laquelle il est connecté.

Exemple montrant les détails de `Volume Attachment Instance Reference` :

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## Déconnexion d'un volume à l'aide de la CLI
{: #detach-vol-attachment-cli}

Utilisez la commande `instance-volume-attachment-detach` pour déconnecter un volume d'une instance et supprimer la connexion du volume. Le volume de stockage par blocs n'est pas supprimé, vous pourrez le [connecter ultérieurement à une autre instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## Suppression d'un volume de stockage par blocs à l'aide de la CLI
{: #delete-vol-cli}

Utilisez la commande `volume-delete` et spécifiez l'ID de volume pour supprimer un volume de stockage par blocs.

**Remarque :** vous ne pouvez pas supprimer un volume de stockage par blocs actif. Vous devez d'abord [le déconnecter du serveur virtuel](#detach-vol-attachment-cli).

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

Exemple :

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

Vous préférez gérer les volumes de stockage par blocs à l'aide de la console {{site.data.keyword.cloud}} ? Pour plus d'informations, voir [Gestion de volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage).
{:tip}

## Etapes suivantes
{: #next-step-managing-block-storage-cli}

[Créez davantage de volumes à l'aide de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

Pour les problèmes liés aux volumes de stockage par blocs existants, vous pouvez peut-être identifier et résoudre les problèmes vous-même. Pour plus d'informations, voir [Traitement des incidents liés au stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
