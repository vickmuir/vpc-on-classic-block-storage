---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Tutoriel d'initiation 
{: #getting-started}

Ce tutoriel vous aide à démarrer la création de volumes {{site.data.keyword.block_storage_is_short}} sur un cloud privé virtuel.

## Avant de commencer
{: #block-storage-before-you-begin}

Pour commencer, examinez d'abord le contenu susceptible de vous aider dans votre mise en oeuvre. Vous êtes novice sur {{site.data.keyword.cloud}} et {{site.data.keyword.block_storage_is_short}} ? Les informations suivantes peuvent vous aider :

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [A propos de Block Storage for VPC ](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

Inscrivez-vous pour obtenir un compte {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Inscription à {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}.

## Etape 1 - Déterminez vos besoins en stockage 
{: #determine-storage-requirements}

Exécutez-vous des charges de travail à usage général avec des besoins de stockage modestes ? Ou bien, vos E-S de charge de travail nécessitent-elles une capacité et des performances supérieures ? Pour savoir comment déterminer la capacité et les performances, voir [Capacité et performances de Block Storage](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance). Voir également [Profils](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) pour savoir quelle option de profil IOPS est celle qui répond le mieux à vos besoins en matière de stockage. 

Créez-vous également une instance de serveur virtuel ? Voir [comment les profils de serveur virtuel sont associés aux profils de stockage](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage).

## Etape 2 - Déterminez la taille et le prix de votre bloc de stockage 
{: #size-price-block-storage}

Sélectionnez un [profil de niveau IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) pour votre volume de stockage par blocs. Si vous avez des exigences de performances bien définies qui ne relèvent pas d'un niveau IOPS prédéfini, vous pouvez également choisir un [profil IOPS personnalisé](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).  

Après avoir choisi la taille et les performances de vos volumes de stockage par blocs, reportez-vous aux informations de [tarification](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing) pour vous aider à chiffrer vos volumes et à comprendre le mode de facturation. 

## Etape 3 - Connectez-vous à votre compte {{site.data.keyword.cloud_notm}} 
{: block-storage-log-into-ibm-account}

Accédez au formulaire de commande {{site.data.keyword.block_storage_is_short}} à partir du catalogue [{{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: external}. Utilisez votre IBMid et votre mot de passe. 

## Etape 4 (facultatif) - Vérifiez l'accès à {{site.data.keyword.vpc_short}}

Si vous souhaitez créer un volume dans un cloud privé virtuel, vous devez d'abord [créer un VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console). Ignorez cette étape si vous souhaitez créer un volume autonome en dehors du VPC. Vous pouvez demander ultérieurement un accès à {{site.data.keyword.vpc_short}} pour accéder à une instance et connecter un volume de stockage par blocs que vous avez créé de manière indépendante. Pour plus d'informations sur {{site.data.keyword.vpc_short}}, voir [Tutoriel d'initiation de Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Etape 5 - Créez des volumes de stockage en mode bloc 

Commencez à créer vos volumes dans la console [{{site.data.keyword.cloud_notm}} (interface utilisateur)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), ou à l'aide de la [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) ou de [l'API {{site.data.keyword.vpc_short}}](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}. Pour plus d'informations sur l'utilisation des outils IBM Cloud Developer pour installer la CLI IBM Cloud, voir [Initiation aux outils IBM Cloud Developer](/docs/cli?topic=cloud-cli-getting-started).

## Etapes suivantes
{: #next-step-block-storage-getting-started}

Après avoir créé le stockage par blocs, explorez d'autres options : 

* [Affichage des détails sur le volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Gestion de vos volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
