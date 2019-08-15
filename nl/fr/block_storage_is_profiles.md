---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Profils {{site.data.keyword.block_storage_is_short}}
{: #block-storage-profiles}

Lorsque vous mettez à disposition des volumes secondaires {{site.data.keyword.block_storage_is_short}} à l'aide de la console, de la CLI ou de l'API {{site.data.keyword.cloud_notm}}, vous spécifiez un profil d'IOPS qui répond le mieux à vos besoins en matière de stockage. Les profils sont disponibles en trois niveaux d'IOPS prédéfinis ou en tant qu'IOPS personnalisées.  Les niveaux d'IOPS offrent des performances d'IOPS/Go garanties pour des volumes allant jusqu'à 2 To. Vous pouvez également spécifier un profil d'IOPS personnalisé et définir une capacité et des IOPS de volume dans une plage.
{:shortdesc}

## Profils IOP hiérarchisés
{: #tiers}

Le stockage par blocs fournit trois niveaux d'IOPS prédéfinis que vous pouvez sélectionner pour spécifier des performances optimales pour vos charges de travail de calcul et éviter les goulots d'étranglement. Vous pouvez mettre à disposition des volumes dans votre zone de disponibilité avec des IOPS garanties, comme décrit dans le tableau suivant :

| Niveau d'IOPS | Charge de travail | Taille de volume | Nb max d'IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/Go | Charges de travail à usage général - Charges de travail hébergeant de petites bases de données pour des applications Web ou stockant des images de disque de machine virtuelle pour un hyperviseur | 10 Go à 1 To | Jusqu'à 3 000 IOPS |
| | | Supérieur à 1 To jusqu'à 2 To | 3 IOPS/Go jusqu'à 6 000 IOPS |
| 5 IOPS/Go | Charges de travail caractérisées par un pourcentage élevé de données actives, telles que des bases de données transactionnelles et autres bases de données sensibles aux performances| 10 Go à 600 Go | Jusqu'à 3 000 IOPS |
| | | Supérieur à 600 Go jusqu'à 2 To | 5 IOPS/Go jusqu'à 10 000 IOPS|
| 10 IOPS/Go | Charges de travail de stockage exigeantes - Charges de travail à forte consommation de données, créées par les bases de données NoSQL, le traitement de données pour la vidéo, l'apprentissage automatique et l'analyse | 10 Go à 300 Go | Jusqu'à 3 000 IOPS |
| | | Supérieur à 300 Go jusqu'à 2 To | 10 IOPS/Go jusqu'à 20 000 IOPS |
{: caption="Tableau 1. Profils de niveau IOPS et niveaux de performances pour chaque niveau" caption-side="top"}

Le débit maximal pour tous les niveaux d'IOPS de stockage par blocs est de 750 Mo/s sur la base d'une taille de bloc de 16 ko

## Profil IOPS personnalisé
{: #custom}

Les IOPS personnalisées sont une bonne option lorsque vous avez des exigences de performances bien définies qui ne relèvent pas d'un niveau d'IOPS prédéfini. Vous pouvez personnaliser l'IOPS en spécifiant le nombre total d'IOPS pour le volume compris dans l'intervalle correspondant à sa taille. Vous pouvez mettre à disposition des volumes de 100 à 20 000 IOPS.

Le tableau suivant présente les plages d'IOPS disponibles en fonction de la taille du volume.

| Taille du volume (Go) | Plage IOPS |
|-------------|--------------|
| 10 -39   | 100 - 1,000 |
| 40 - 79 | 100 -2,000 |
| 80 - 99 | 100 - 4,000 |
| 100 - 499 | 100 - 6,000 |
| 500 - 999 | 100 - 10,000 |
| 1,000 - 1,999 | 100 - 20,000 |
{: caption="Tableau 2. IOPS disponibles en fonction de la taille du volume" caption-side="top"}

## Comment les profils de serveur virtuel sont associés aux profils de stockage
{: #vsi-profiles-relate-to-storage}

Les profils de serveur virtuel sont une combinaison d'UC virtuelle et de mémoire RAM pouvant être instanciée rapidement pour démarrer une instance de serveur virtuel.  Vous choisissez parmi [trois familles de profils](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)
en fonction de vos exigences en matière de charge de travail.  Ces exigences peuvent aller des charges de travail courantes aux charges de travail à forte consommation d'UC ou de mémoire.  

De même, les profils de stockage (niveaux d'IOPS ou personnalisés) offrent une gamme de capacités et de performances pour les volumes secondaires.  Par défaut, 
un volume d'amorçage principal de 100 Go est créé lorsque vous créez une instance de serveur virtuel.  Vous pouvez également créer et connecter des volumes secondaires.  
Lorsque vous créez un volume de données secondaire dans le cadre de la création d'instance, vous sélectionnez un profil de stockage qui répond le mieux à vos exigences de stockage
pour vos charges de travail de calcul. En général, à mesure que vos besoins en calcul augmentent, des performances IOPS plus élevées sont nécessaires.  Le tableau suivant illustre cette relation.

| Profil de stockage des niveaux d'IOPS | Profil de serveur virtuel |
|-----------------|------------------------|
| 3 IOPS/Go       | [Balanced](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) pour des charges de travail courantes |
| 5 IOPS/Go       | [Compute](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) pour des exigences d'UC intensives |
| 10 IOPS/Go      | [Memory](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) pour les charges de travail à forte consommation de mémoire |
{: caption="Tableau 3. Relation entre les profils de stockage par blocs et les profils de serveur virtuel" caption-side="top"}

## Affichage des profils IOPS
{: #view-iops-profiles}

Vous pouvez afficher les profils d'IOPS disponibles dans la console, la CLI ou l'API {{site.data.keyword.cloud_notm}}.

### Utilisation de la console IBM Cloud
{: using-console-iops-profile}

 Lorsque vous [créez un volume de stockage par blocs à partir de la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), sélectionnez **Niveaux** dans le menu déroulant.

 Vous pouvez aussi sélectionner **Personnalisé**, puis sélectionner une valeur IOPS dans la plage de cette taille de volume. Cliquez sur le lien de taille de stockage pour afficher un tableau des plages de tailles et d'IOPS.

 ### Utilisation de l'interface de ligne de commande (CLI)
 {: using-cli-iops-profiles}

 Pour afficher la liste des profils disponibles à l'aide de la CLI, exécutez la commande suivante :
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### Utilisation de l'API
{: using-api-iops-profiles}

La demande d'API cURL suivante extrait tous les profils de volume.

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## Informations connexes

Pour plus d'informations sur les profils Balanced, Compute et Memory pour {{site.data.keyword.vsi_is_short}}, voir [Profils](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).
