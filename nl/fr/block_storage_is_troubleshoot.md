---

copyright:
  years: 2019
lastupdated: "2018-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot

subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Identification et résolution des incidents liés à {{site.data.keyword.block_storage_is_short}}
{: #troubleshoot}

Il est possible que vous rencontriez des problèmes lors de la création ou de la gestion de {{site.data.keyword.block_storage_is_short}}. Mais, vous pouvez bien souvent les résoudre en effectuant quelques étapes simples. Les problèmes, symptômes, causes probables et solutions sont décrits dans les sections suivantes.
{:shortdesc}

## Impossible d'extraire un volume dans une région spécifiée
{: #troubleshoot-topic-1}

Les informations sur un ou plusieurs volumes de stockage par blocs ne peuvent pas être extraites pour une région donnée.
{: tsSymptoms}

L'une des causes suivantes peut s'appliquer :

* Le nom et les informations du volume sont manquants dans la sortie de l'interface utilisateur ou de la CLI.
* Vous tentez peut-être d'accéder à un volume situé dans une région autre que la vôtre.
* Vous tentez peut-être d'accéder à un volume de génération 2.
{: tsCauses}

Vérifiez que le volume n'a pas été déconnecté d'une instance de serveur virtuel et supprimé. Recherchez l'instance à laquelle vous avez connecté le volume en dernier dans la liste de toutes les instances de serveur virtuel :

1. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, accédez à **l'icône Menu![Icône Menu](../../icons/icon_hamburger.svg) > Calcul > Instances de serveur virtuel**.

1. Sélectionnez une instance de serveur virtuel dans la liste de tous les serveurs virtuels.

Si le volume n'est pas connecté comme prévu et n'apparaît pas dans la liste des volumes, il a probablement été supprimé.  Etant donné que la suppression d'un volume supprime complètement ses données, il ne peut pas être restauré.  

Si vous utilisez l'interface de ligne de commande, vérifiez que vous avez entré la syntaxe correcte pour afficher les volumes. Voir [Affichage de tous les volumes de stockage par blocs à partir de la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli). Vérifiez que vous avez spécifié le groupe de ressources ou la zone appropriés.
{: tsResolve}

## Impossible de supprimer un volume par son nom ou son identifiant
{: #troubleshoot-topic-2}

Vous ne pouvez pas supprimer un volume de stockage par blocs par son nom ou par son ID.
{: tsSymptoms}

Le nom et l'ID du volume ne sont pas acceptés.
{: tsCauses}

Vérifiez que le nom ou l'identificateur du volume est correct et que le volume n'est pas connecté à une instance de serveur virtuel. Vérifiez également que le volume n'est pas en attente.
{: tsResolve}
