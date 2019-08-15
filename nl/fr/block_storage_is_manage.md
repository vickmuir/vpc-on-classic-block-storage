---

copyright:
  years: 2019
lastupdated: "2019-07-11"

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

# Gestion de volumes de stockage par blocs à l'aide de l'interface utilisateur
{: #managing-block-storage}

Gérez {{site.data.keyword.block_storage_is_short}} à partir de l'interface utilisateur. Détachez un volume d'une instance de serveur virtuel, transférez un volume d'une instance à une autre, joignez un volume précédemment attaché, renommez un volume, définissez la suppression automatique du volume, supprimez manuellement un volume ou affectez un accès à un volume.
{:shortdesc}

## Déconnexion d'un volume de stockage par blocs d'une instance de serveur virtuel
{: #detach}

Vous pouvez déconnecter un volume de données de stockage par blocs relié à une instance de serveur virtuel.  La déconnexion libère le volume pour qu'il soit utilisé par une autre instance.

Pour déconnecter un volume :

1. Accédez à la liste de tous les volumes de stockage par blocs. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Block storage**.
1. Recherchez le volume, puis cliquez sur les points de suspension (...) situés à la fin de la ligne du tableau. Un menu contextuel s'affiche.
1. Dans le menu, cliquez sur **Dissocier de l'instance**.
1. Confirmez en cliquant sur **Dissocier l'instance** dans la fenêtre contextuelle.

Vous pouvez également cliquer sur un volume individuel dans la liste de tous les volumes de stockage par blocs et accéder à la page **Détails du volume** pour ce volume. Sous **Instances connectées**, cliquez sur le signe moins en regard de l'instance de serveur virtuel pour déconnecter le volume de cette instance.

## Transfert d'un volume de stockage par blocs d'une instance de serveur virtuel à une autre
{: #transfer}

Pour transférer un volume de stockage par blocs vers une autre instance de serveur virtuel :

1. [Déconnectez le volume de son instance de serveur virtuel](#detach).
1. Accédez à l'instance de serveur virtuel sur laquelle vous souhaitez transférer le volume. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Calcul > Instances de serveur virtuel**.
1. Sélectionnez un serveur virtuel dans la liste.
1. Sous Volumes de stockage connectés, cliquez sur le signe plus pour ajouter un volume. Tous les volumes de stockage par blocs sont affichés.
1. Dans la liste des volumes, sélectionnez le volume que vous avez déconnecté.

## Connexion d'un volume de stockage par blocs précédemment connecté
{: #reattach}

Les volumes de stockage par blocs sont connectés par défaut lorsque vous créez une nouvelle instance de serveur virtuel.  Lorsque vous déconnectez un volume d'une instance, il existe en tant que volume déconnecté et s'affiche dans la liste de [tous les volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). Vous pouvez le connecter à une autre image à partir de la liste des volumes de stockage par blocs.

1. Accédez à la liste de tous les volumes de stockage par blocs. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Block storage**.
1. Recherchez le volume, puis cliquez sur les points de suspension (...) situés à la fin de la ligne du tableau. Un menu contextuel s'affiche.
1. Dans le menu, cliquez sur **Connecter à l'instance**.
1. Sélectionnez une instance de serveur virtuel disponible.
1. Confirmez votre sélection.

## Renommage d'un volume de stockage par blocs
{: #rename}

Vous pouvez modifier le nom d'un volume existant pour le rendre plus significatif.

1. Accédez à la liste de tous les volumes de stockage par blocs. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Block storage**.
1. Recherchez le volume, puis cliquez sur le nom du volume pour accéder à la page Détails du volume.
1. Cliquez sur l'icône en forme de crayon après le nom du volume et modifiez le nom du volume.
1. Confirmez votre modification.

## Suppression d'un volume de stockage par blocs
{: #delete}

La suppression d'un volume de stockage par blocs supprime complètement ses données. Le volume ne peut pas être restauré.

Vous ne pouvez pas supprimer un volume de stockage par blocs actif. Pour supprimer un volume, [déconnectez-le](#detach) d'abord du serveur virtuel, puis procédez comme suit :

1. Accédez à la liste de tous les volumes de stockage par blocs. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Block storage**.
1. Localisez le volume que vous souhaitez supprimer, puis cliquez sur les points de suspension à la fin de la ligne du tableau. Un menu contextuel s'affiche.
1. Dans le menu, cliquez sur **Supprimer**.
1. Confirmez la suppression.

## Suppression automatique des volumes de données de stockage par blocs
{: #auto-delete}

A l'aide de la fonction Suppression automatique, vous pouvez spécifier qu'un volume de données de stockage par blocs soit automatiquement supprimé lorsque vous supprimez une instance à laquelle il est connecté. Cette fonctionnalité ne s'applique pas aux volumes d'amorçage et est désactivée par défaut.

Pour activer la suppression automatique pour un volume de stockage par blocs existant connecté à une instance, procédez comme suit :

1. Localisez l'instance de serveur virtuel à laquelle le volume est connecté. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for the Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Calcul > Instances de serveur virtuel**.
1. Sous **Volumes de stockage par blocs connectés**, sélectionnez un volume.
1. Dans le menu contextuel, cliquez sur le bouton Suppression automatique pour l'activer.
1. Confirmez votre sélection.

Vous pouvez également commencer par sélectionner un volume dans la liste des volumes de stockage par blocs (**Stockage > Block storage**).

Pour activer la suppression automatique sur un nouveau volume lors de la création d'une instance, voir [Création et connexion d'un volume de stockage par blocs lorsque vous créez une instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi).

## Affectation de l'accès à un volume de stockage par blocs
{: #assign-volume-access}

Avec les privilèges d'administrateur, vous pouvez attribuer un accès utilisateur au niveau du volume au service {{site.data.keyword.block_storage_is_short}}. Le tableau suivant présente les informations que vous devez fournir dans [l'interface utilisateur IAM (Identity and Access Management)](/docs/iam?topic=iam-account_setup#assigning-access).

| Zone IAM | Action |
|--------|-------------|
| Services | Sélectionnez **Services d'infrastructure** |
| Type de ressource | Sélectionnez **Block Storage for VPC** |
| ID volume | Entrez l'[ID volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) pour attribuer l'accès à un volume spécifique. |
| Sélectionner des rôles | Attribuez les rôles d'accès à la plateforme, généralement Opérateur |
{: caption="Tableau 1. Informations relatives à IAM" caption-side="top"}

Pour plus d'informations, consultez les [bonnes pratiques de l'attribution d'accès](/docs/iam?topic=iam-account_setup#account_setup). Pour plus d'informations sur le processus IAM complet, qui inclut l'invitation d'utilisateurs sur votre compte et l'attribution d'un accès Cloud IAM, voir [Tutoriel d'initiation d'IAM](/docs/iam?topic=iam-getstarted#getstarted).

## Statut du volume de stockage par blocs
{: #status}

Le tableau suivant indique les statuts que vous pourriez rencontrer lors de la création, de l'affichage ou de la gestion de vos volumes de stockage par blocs.

| Statut | Signification |
|--------|-------------|
| Disponible | Un volume a été extrait |
| | Un volume est disponible et peut être connecté à une instance |
| | Un volume connecté est disponible pour les données
| | Un volume d'amorçage est disponible |
| Echec    | La création de volume a échoué |
| | Tous les volumes d'une région n'ont pas pu être extraits |
| | Impossible de trouver un volume avec l'ID volume spécifié |
| | Un volume n'a pas pu être supprimé |
| En attente | Un volume est en cours de création |
| | Un volume est connecté à une instance |
| Suppression en attente | Un volume est en cours de suppression |
{: caption="Tableau 2. Etats de stockage par blocs" caption-side="top"}

Vous préférez gérer les volumes de stockage par blocs à l'aide de l'interface CLI ? Pour plus d'informations, voir [Gestion de volumes de stockage par blocs (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli).
{: tip}

## Etapes suivantes
{: #next-step-managing-block-storage}

Vous pouvez [créer des volumes supplémentaires](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

Pour les problèmes liés aux volumes de stockage par blocs existants, vous pouvez peut-être identifier et résoudre les problèmes vous-même. Pour plus d'informations, voir [Traitement des incidents liés au stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
