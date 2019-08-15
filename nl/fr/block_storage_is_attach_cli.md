---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, CLI, block storage volume, volume, volume attachment, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Connexion d'un volume de stockage par blocs à l'aide de la CLI
{: #attaching-block-storage-cli}

Une connexion à un volume relie un volume {{site.data.keyword.block_storage_is_short}} à une instance de serveur virtuel. Chaque instance peut comporter [plusieurs connexions de volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits), mais une seule connexion relie un volume à une instance.
{:shortdesc}

## Avant de commencer
{: #before-attaching-block-storage-cli}

1. Assurez-vous d'avoir téléchargé, installé et initialisé les plug-ins CLI suivants :
    * Interface CLI d'{{site.data.keyword.cloud_notm}}
    * Plug-in infrastructure-service

   Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Lorsque vous installez le plug-in vpc-infrastructure pour la première fois, vous devez définir la génération cible sur gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assurez-vous que vous avez déjà [créé une instance {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Connexion d'un volume de stockage par blocs à l'aide de la CLI
{: #attach-block-storage-cli}

Pour connecter un volume à une instance de serveur virtuel du groupe de ressources en cours, exécutez la commande suivante.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` est le nom que vous indiquez pour la connexion de volume et INSTANCE_ID est l'ID de la VSI.

`VOLUME_ID` spécifie le volume que vous connectez.

Spécifiez `--auto-delete true` si vous souhaitez que le volume soit automatiquement supprimé lors de la suppression de la VSI.

Pour afficher une liste des instances de serveur virtuel disponibles, exécutez la commande `ibmcloud is instances`.

Exemple :

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.xxx.xx.xx    -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.xxx.xx.x     -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             192.xxx.xxx.xx   -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             192.xxx.xxx.xxx  -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## Affichage des détails d'un volume connecté à une instance de serveur virtuel
{: #show-details-attached-vol}

Après avoir connecté un volume, vous pouvez afficher les détails en spécifiant l'ID d'instance et l'ID de la connexion de volume dans la commande `instance-volume-attachment`.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## Affichage de toutes les connexions de volume d'une instance de serveur

Utilisez la commande `instance-volume-attachments` et spécifiez l'ID d'instance pour afficher toutes les connexions de volumes à une instance.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

Vous préférez utiliser la console {{site.data.keyword.cloud}} ? Pour plus d'informations sur la manière dont les volumes sont connectés à partir de la console, voir [Connexion de volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).
{:tip}

## Création d'un fichier JSON de connexion de volume
{: #volume_attachment_json}

Lorsque vous mettez à disposition une instance de serveur virtuel à l'aide de la CLI et créez un volume de stockage par blocs dans le cadre du processus, vous devez spécifier un fichier JSON de connexion de volume. Le fichier JSON de connexion de volume, spécifié dans la commande ou sous forme de fichier, définit les paramètres de volume. Lorsque vous [créez une instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) et spécifiez le paramètre `--volume-attach`, vous spécifiez le fichier JSON du volume. Par exemple, `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

Voici un exemple de fichier JSON de connexion de volume qui définit un volume personnalisé :

```
[
    {
        "name": "myvolume-attachment",
        "delete_volume_on_instance_delete": true,
        "volume": {
            "name": "myvolume",
            "capacity": 100,
            "iops": 1000,
            "profile": {
                "name": "custom"
            }
        }
    }
]
```
{: screen}

## Etapes suivantes
{: #next-step-attaching-block-storage-cli}

Créez des volumes supplémentaires et gérez les volumes existants.  Voir les informations suivantes.

* [Création d'un volume de stockage par blocs à l'aide de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [Gestion de volumes de stockage par blocs à l'aide de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
