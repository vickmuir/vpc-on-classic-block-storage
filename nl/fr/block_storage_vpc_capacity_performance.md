---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

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

# Capacité et performances de {{site.data.keyword.block_storage_is_short}}
{: #capacity-performance}

Le choix de la taille de volume et du niveau de performance optimaux pour le stockage par blocs pour vos charges de travail est important. Lorsque vous mettez à disposition des volumes {{site.data.keyword.block_storage_is_short}} à partir de l'interface utilisateur ou de l'interface CLI, vous pouvez choisir la capacité de votre volume ainsi que son niveau de performance.
{:shortdesc}

## Capacité
{: #block-storage-vpc-capacity}

Vous pouvez spécifier une capacité de 10 Go à 2 000 Go (2 To) par volume de données de stockage par blocs, par incréments de 1 Go. La capacité de volume totale est déterminée lorsque vous sélectionnez un [profil IOPS](#iops-profiles). Les volumes d'amorçage sont de 100 Go.

## Profils IOPS
{: #iops-profiles}

Lorsque vous mettez à disposition des volumes {{site.data.keyword.block_storage_is_short}}, vous spécifiez un [profil IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) qui répond le mieux à vos besoins en matière de stockage. Les profils sont disponibles en trois niveaux d'IOPS prédéfinis ou en tant qu'IOPS personnalisées. Les [niveaux d'IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) offrent des performances d'IOPS/Go garanties pour des volumes allant jusqu'à 2 To. Vous pouvez également spécifier un profil d'[IOPS personnalisé](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) et définir une capacité et des IOPS de volume dans une plage. Utilisez la console, la CLI ou l'API {{site.data.keyword.cloud_notm}} pour spécifier un profil.

## Comment la taille des blocs affecte les performances
{: #how-block-size-affects-performance}

Une IOPS est basée sur une taille de bloc de 16 ko avec une charge de travail aléatoire 50/50 en lecture/écriture à 50 %. Un bloc de 16 ko équivaut à une écriture sur le volume. Le débit de référence est déterminé par la quantité d'IOPS multipliée par la taille de bloc de 16 ko. Plus le nombre d'IOPS que vous spécifiez est élevé, plus le débit est élevé. Le débit maximal pour un volume de stockage par blocs est de 750 Mo/s.

La taille de bloc que vous choisissez pour votre application a une incidence directe sur les performances de stockage. Si la taille de bloc est inférieure à 16 ko, la limite d'IOPS est atteinte avant la limite de débit. Inversement, si la taille de bloc est supérieure à 16 ko, la limite de débit est atteinte avant la limite d'IOPS. Le tableau suivant fournit des exemples de l'impact de la taille de bloc et des opérations d'entrée-sortie par seconde sur le débit (taille E-S moyenne calculée x IOPS = débit en Mo/s).

| Taille de bloc (ko) | IOPS | Débit (Mo/s) |
|-----------------|------|-------------------|
| 4 (standard pour Linux) | 1 000 | 4 |
| 8 (standard pour Oracle) | 1 000  | 8 |
| 16 | 1 000 | 16 |
| 32 (standard pour SQL Server) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="Tableau 1. Exemples de l'impact de la taille de bloc et des opérations d'entrée-sortie par seconde sur le débit" caption-side="top"}
