---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, block storage volume, volume, volume attachment, virtual server instance, instance

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

# Connexion d'un volume de stockage par blocs à l'aide de l'interface utilisateur
{: #attaching-block-storage}

Lorsque vous créez un volume {{site.data.keyword.block_storage_is_short}} pour une instance de serveur virtuel à partir de l'interface utilisateur, le volume est connecté à l'instance par défaut. Lorsque vous déconnectez un volume, il existe en tant que volume non connecté que vous pouvez reconnecter ultérieurement. Ces volumes disponibles sont affichés dans la liste de [tous les volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). Vous pouvez connecter le volume à une autre instance à partir de la liste de tous les volumes de stockage par blocs ou lors de la visualisation de détails sur une instance particulière.
{:shortdesc}

## Limites de connexion de volume
{: #vol-attach-limits}

Bien que vous ne puissiez connecter qu'un seul volume de stockage par blocs à une instance de serveur virtuel à la fois, vous pouvez connecter plusieurs volumes de stockage par blocs différents à une seule instance, avec les limites suivantes :

* Les instances équipées de moins de 4 UC virtuelles acceptent jusqu'à 4 volumes secondaires de stockage par blocs, plus le volume d'amorçage.
* Les instances équipées de 4 UC virtuelles ou plus acceptent jusqu'à 12 volumes secondaires de stockage par blocs, plus le volume d'amorçage.

## Connexion d'un volume de stockage par blocs à une instance de serveur virtuel
{: #attach}

Dans la liste de tous les volumes de stockage par blocs, procédez comme suit.

1. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Block storage**.
1. Dans la liste des volumes, cliquez sur l'elipsis à la fin d'une ligne pour afficher un volume disponible et non connecté.  Un menu d'action contextuel s'affiche.
1. Sélectionnez **Connecter à l'instance**.
1. Sélectionnez une ressource de calcul (instance de serveur virtuel) dans la liste des ressources disponibles, puis cliquez sur **Connecter**.
1. Les messages s'affichent sur la page de détails du volume, indiquant que le volume est connecté à l'image.  Une fois l'opération terminée, le nom de l'image apparaît sous **Instances connectées**.

Vous pouvez également connecter un volume de stockage par blocs à partir de la page de détails de l'instance de serveur virtuel.

1. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Calcul > Instances de serveur virtuel**.
1. Sélectionnez une instance dans la liste de toutes les instances de serveur virtuel. Si des volumes de stockage par blocs sont connectés, ils apparaissent sous **Volumes de stockage par blocs connectés**.
1. Sélectionnez **Connecter un volume**.
1. Sélectionnez un volume dans la liste des ressources disponibles, puis cliquez sur **Connecter**. Les messages s'affichent sur la page de détails de l'instance, indiquant que le volume est connecté.  Une fois cette opération terminée, la liste des **Volumes de stockage par blocs connectés** est mise à jour pour inclure le nouveau volume.

Vous pouvez également connecter manuellement des volumes de stockage par blocs à l'aide de la CLI. Pour plus d'informations, voir [Connexion de volumes de stockage par blocs (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
{: tip}

## Etapes suivantes
{: #next-step-attaching-block-storage}

Créez des volumes supplémentaires et gérez les volumes existants. Voir les informations suivantes.

* [Création de volumes de stockage par blocs dans la console IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gestion de volumes de stockage par blocs à l'aide de l'interface utilisateur](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
