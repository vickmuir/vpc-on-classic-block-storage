---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Création de volumes de stockage par blocs dans la console {{site.data.keyword.cloud_notm}}
{: #creating-block-storage}
[comment]: # (rubrique d'aide liée)

Vous pouvez créer un volume de stockage par blocs lorsque vous créez une instance de serveur virtuel ou si vous créez un volume autonome à associer ultérieurement à une instance.
{:shortdesc}

Avant de commencer, veillez à [créer un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Création et connexion d'un volume de stockage par blocs lors de la création d'une instance 
{: #create-from-vsi}

1. Créez une instance. Dans la [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} pour Virtual Private Cloud, accédez à **l'icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Calcul > Instances de serveurs virtuels pour VPC > Nouvelle instance**.
1. [Configurez une instance de serveur virtuel](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers). Sous **Volumes de stockage par blocs connectés**, sélectionnez **Nouveau volume de stockage par blocs**.
1. Entrez les informations décrites dans le tableau suivant. Lorsque vous avez terminé, cliquez sur **Créer un volume**.

| Zone | Valeur |
|-------|-------|
| Nom | Spécifiez un nom significatif pour le volume, par exemple un nom décrivant la fonction de calcul ou de charge de travail. Vous pouvez saisir une combinaison de caractères alphanumériques et modifier le nom ultérieurement si vous le souhaitez. |
| Profil | Sélectionnez [Niveaux](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) et sélectionnez le niveau de performance souhaité dans la liste des IOPS. Si vos exigences de performances ne correspondent pas à un niveau IOPS prédéfini, sélectionnez [Personnalisé](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom), puis sélectionnez une valeur IOPS comprise dans la plage de cette taille de volume. Cliquez sur le lien de **taille de stockage** pour afficher un tableau des plages de tailles et d'IOPS. |
| Suppression automatique | Activez cette fonctionnalité pour supprimer automatiquement ce volume lorsque l'instance de serveur virtuel connectée est supprimée. Vous pouvez modifier ce paramètre ultérieurement dans la page de détails du serveur virtuel. |
| IOPS | Sélectionnez 3, 5 ou 10 IOPS/Go pour un profil hiérarchisé |
| Taille | Entrez une taille de volume en Go. Les tailles de volume peuvent être comprises entre 10 Go et 2 To. |
| Chiffrement | Le chiffrement à l'aide de clés gérées par IBM est activé par défaut sur tous les volumes. Vous pouvez également choisir le chiffrement **Géré par le client** et utiliser votre propre clé de chiffrement. Pour connaître les conditions préalables et les étapes de configuration du chiffrement géré par le client, voir [Création de volumes de stockage par blocs avec un chiffrement géré par le client](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Tableau 1. Valeurs de volume de stockage par blocs spécifiées lors de la mise à disposition d'une instance" caption-side="top"}

Un volume de stockage par blocs est créé et connecté à l'instance de serveur virtuel. Sur la page de détails de l'instance, la liste des **Volumes de stockage par blocs connectés** est mise à jour pour afficher le nouveau volume. 

Un volume de stockage par blocs ne peut être connecté qu’à un seul serveur virtuel à la fois. Sur la page de récapitulatif du volume de stockage par blocs, vous pouvez afficher des détails sur l'instance de serveur virtuel en sélectionnant le nom de l'instance sous **Instances connectées**. 

## Création d'un volume de stockage par blocs autonome 
{: #create-standalone-vol}

Vous pouvez créer un volume de stockage par blocs indépendamment de la mise à disposition du serveur virtuel et le connecter à une instance ultérieurement. 

1. Dans la [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} for Virtual Private Cloud, accédez à **l'icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Stockage > Volumes Block Storage for VPC** et sélectionnez **Nouveau volume**.
1. Entrez les informations dans le tableau ci-dessous pour définir le nouveau volume de stockage par blocs. 
1. Lorsque vous avez terminé, cliquez sur **Créer un volume**. Vous revenez à la page Volume de stockage par blocs, où un message indique que le volume est en cours de création. Un deuxième message s'affiche lorsque le volume est créé. 
1. Pour afficher les détails du nouveau volume, sélectionnez le lien **Afficher la ressource** dans le deuxième message pour accéder à la page Détails du volume. 

| Zone | Valeur |
|-------|-------|
| Nom | Indiquez un nom explicite pour votre volume. Par exemple, indiquez un nom décrivant la fonction de calcul ou de charge de travail. Vous pouvez entrer jusqu'à 40 caractères alphanumériques et éditer le nom ultérieurement. |
| Groupe de ressources | Indiquez un groupe de ressources. Les groupes de ressources permettent d'organiser vos ressources de compte pour le contrôle d'accès et la facturation. Pour plus d'informations sur la configuration d'un groupe de ressources, voir [Meilleures pratiques pour l'organisation des ressources dans un groupe de ressources](/docs/resources?topic=resources-bp_resourcegroups#setuprgs).|
| Etiquettes | Spécifiez une étiquette pour organiser vos ressources. Une étiquette est un libellé affecté à une ressource pour un filtrage simple des ressources de votre liste de ressources. Pour plus d'informations sur les étiquettes, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag). |
| Emplacement | Zone de disponibilité dans votre région, héritée du VPC (par exemple, US South 1). |
| Taille | Entrez une taille de volume en Go. Les tailles de volume peuvent être comprises entre 10 Go et 2 To. |
| IOPS | Sélectionnez [Niveaux d'E-S/s](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) et sélectionnez la vignette contenant le niveau de performance souhaité. |
| Personnalisé |En fonction de la taille du volume que vous avez spécifié, sélectionnez une valeur IOPS dans la plage de cette taille de volume. Cliquez sur le lien de **taille de stockage** pour afficher un tableau des plages de tailles et d'IOPS. Pour plus d'informations, voir [Profils IOPS personnalisés](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). |
| Chiffrement | Le chiffrement à l'aide de clés gérées par IBM est activé par défaut sur tous les volumes. Pour utiliser vos propres clés de chiffrement, choisissez une option de chiffrement gérée par le client. Pour plus d'informations, voir [Création de volumes de stockage par blocs avec un chiffrement géré par le client](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).|
{: caption="Tableau 2. Valeurs de définition d'un volume de stockage par blocs " caption-side="top"}

Vous préférez créer des volumes de stockage par blocs à l'aide de l'interface CLI ? Pour plus d'informations, voir [Création de volumes de stockage par blocs à l'aide de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).
{: tip}

## Etapes suivantes
{: #next-step-creating-block-storage}

Lorsque vous actualisez la page Volumes de stockage par blocs, le nouveau volume apparaît en tête de la liste des volumes. Si le volume a été créé avec succès, il affiche le statut Disponible. Pour les volumes autonomes, la colonne Type de connexion est vide (-). Le menu Action (...) situé à la fin d'une ligne de tableau fournit un lien permettant de [connecter un volume de stockage par blocs à une instance](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Vous pouvez continuer à créer davantage de volumes de stockage par blocs ou gérer des volumes existants. 

* [Affichage des détails sur un volume de stockage par blocs ](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Déconnexion d'un volume d'une instance de serveur virtuel](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach) 
* [Suppression d'un volume de stockage par blocs ](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
