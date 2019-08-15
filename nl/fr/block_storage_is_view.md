---

copyright:
  years: 2019
lastupdated: "2019-07-24"

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

# Affichage des détails de volume de stockage par blocs
{: #viewing-block-storage}

Affichez des détails sur un volume {{site.data.keyword.block_storage_is_short}} ou des informations récapitulatives sur tous les volumes.
{:shortdesc}

## Affichage d'informations sur tous les volumes de stockage par blocs
{: #viewvols}

Accédez à la liste des volumes de stockage par blocs. Dans la console [{{site.data.keyword.cloud_notm}} ](https://{DomainName}/vpc){: external} pour Virtual Private Cloud, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Block Storage**.

Par défaut, les volumes de stockage par blocs s'affichent pour tous les groupes de ressources de votre région.  La liste **Block storage for VPC volumes** contient les informations suivantes.

| Zone | Description |
|-------|-------------|
| Statut | Statut du volume, qui sert de filtre par défaut pour toutes les lignes. Pour plus d'informations sur les statuts de volume, voir [Statuts de volume de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status). |
| Nom | Cliquez sur le nom du volume pour afficher les détails de chaque volume. |
| Groupe de ressources | Groupes de ressources définis lors de la configuration de votre VPC. Les groupes de ressources permettent d'organiser vos ressources de compte pour le contrôle d'accès et la facturation. Pour plus d'informations, voir [Meilleures pratiques pour organiser des ressources dans un groupe de ressources](docs/resources?topic=resources-bp_resourcegroups). |
| Emplacement | Zone de disponibilité dans votre région, héritée du VPC (par exemple, US South 1). |
| Taille | Taille du volume que vous avez spécifié, en Go. |
| Nb max d'IOPS | Nombre maximal d'IOPS disponibles sur le volume, défini par le niveau d'IOPS à usage général ou la valeur d'IOPS personnalisée que vous avez spécifiée. |
| Type de connexion | Données, pour un volume secondaire connecté à une instance, amorçage si le volume est connecté en tant que volume d'amorçage ou vide pour un volume non connecté. |
| Chiffrement | Géré par le fournisseur ou [géré par le client](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
| Actions (...) | Cliquez sur les points de suspension pour afficher un menu d'actions spécifiques à votre contexte que vous pouvez effectuer.  Par exemple, un volume disponible non connecté présente des options de menu permettant de le connecter à une instance ou de le supprimer. |
{: caption="Tableau 1. Détails sur tous les volumes" caption-side="top"}

Par défaut, 10 volumes sont affichés dans la liste de tous les volumes de stockage par blocs. Modifiez cette valeur par défaut en cliquant sur la flèche vers le bas et augmentez la liste à 20 ou 50 volumes. Utilisez les flèches situées dans l'angle inférieur droit pour passer à la page suivante et revenir.

## Affichage des détails sur un volume de stockage par blocs
{: #view-vol-details}

Pour afficher des informations détaillées sur un volume de stockage par blocs, accédez à la liste de tous les volumes de stockage par blocs et sélectionnez un volume.  Pour un seul volume, les informations suivantes apparaissent.

| Zone | Description |
|-------|-------------|
| Nom  | Nom que vous avez indiqué lorsque vous avez créé le volume. Cliquez sur l'icône en forme de crayon pour modifier ce nom. |
| Groupe de ressources | Groupe de ressources défini lors de la configuration de votre VPC. Les groupes de ressources gèrent l'accès aux ressources mais n'affectent pas la facturation ou la surveillance. |
| Groupe de ressources | Sélectionnez un groupe de ressources auquel associer le volume.  Les groupes de ressources vous aident à organiser des ressources pour l'accès et la facturation. |
| Type de connexion | Données, pour un volume secondaire connecté à une instance, amorçage si le volume est connecté en tant que volume d'amorçage ou vide pour un volume non connecté. |
| ID | ID de volume généré par le système. |
| Créé | Date générée par le système lorsque le volume a été créé. |
| Emplacement | Zone de disponibilité dans votre région. |
| Taille | Taille du volume que vous avez spécifié. |
| Profil | Niveau d'IOPS ou profil d'IOPS personnalisé. |
| Nb max d'IOPS | Valeur d'IOPS maximale pour un niveau d'IOPS prédéfini ou valeur que vous avez spécifiée pour des IOPS personnalisées. |
| Débit | Performances qu'un disque peut offrir, mesurées en gigabits/seconde (Gb/s).  En fonction du profil du volume, le débit correspond à la quantité de taille de bloc d'IOPS * 16 ko. |
| Chiffrement | Géré par le fournisseur ou géré par le client. |
{: caption="Tableau 2. Détails du volume" caption-side="top"}

Les volumes connectés à une instance de serveur virtuel sont affichés sous **Instances connectées** dans la page **Détails du volume**.  Vous pouvez également [connecter un volume à une instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Pour un volume connecté à une instance, vous pouvez également accéder aux informations relatives à l'instance, puis revenir à la liste de tous les volumes de stockage par blocs.

## Affichage des détails de volume de stockage par blocs connecté dans les détails d'instance

Vous pouvez afficher des informations sur un volume de stockage par blocs connecté à partir de la page **Détails de l'instance de serveur virtuel** :

1. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, accédez à **Icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Calcul > Instances de serveur virtuel** et sélectionnez une instance.
1. Sous **Volumes de stockage par blocs connectés**, cliquez sur le nom d'un volume pour accéder à la page de détails de volume.

Vous préférez afficher les volumes de stockage par blocs à l'aide de l'interface CLI ? Pour plus d'informations, voir [Affichage de volumes de stockage par blocs (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli).
{: tip}

## Etapes suivantes
{: #next-step-viewing-block-storage}

Créez d'autres volumes ou gérez vos volumes de stockage par blocs existants.

* [Création de volumes de stockage par blocs dans la console IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gestion de volumes de stockage par blocs à l'aide de l'interface utilisateur](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
