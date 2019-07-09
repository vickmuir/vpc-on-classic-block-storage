---

copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# Service Block Storage for VPC - Foire aux questions 
{: #block-storage-vpc-faq}

## Comment allouer de la mémoire à mes instances ? 
{: faq}

Lorsque vous créez une instance de serveur virtuel, vous pouvez [créer un volume de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi) que vous connectez à cette instance. Vous pouvez également [créer des volumes autonomes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol), puis les connecter à vos instances ultérieurement. 

## Combien d'instances peuvent partager un volume de stockage par blocs mis à disposition ? 
{: faq}

Un volume de stockage par blocs ne peut être connecté qu’à une seule instance à la fois. Les instances ne peuvent pas partager le même volume. 

## Combien de volumes (données) secondaires de stockage par blocs peuvent être connectés à une instance ? 
{: faq}

Les instances équipées de moins de 4 UC virtuelles acceptent jusqu'à 4 volumes secondaires de stockage par blocs. 

Les instances équipées de 4 UC virtuelles ou plus acceptent jusqu'à 12 volumes secondaires de stockage par blocs. 

## Lors de la mise à disposition des IOP, les IOPS attribuées sont-ils appliqués par instance ou par volume ? 
{: faq}

Les IOPS sont appliquées au niveau du volume. 

## Comment sont mesurées les IOPS ? 
{: faq}

Les IOPS sont mesurées sur la base d'un profil de charge de blocs de 16 ko avec 50% de lectures et 50% d'écritures en mode aléatoire. Les charges de travail qui diffèrent de ce profil sont susceptibles de connaître des performances moins élevées.

## Que sont les profils d'IOPS ? 
{: faq}

Les profils d'IOPS définissent les performances IOPS/Go pour des volumes de capacités différentes. Vous pouvez sélectionner trois [niveaux d'IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) prédéfinis qui offrent des performances d'IOPS garanties afin de répondre aux exigences de votre charge de travail. Vous pouvez également définir des [IOPS personnalisées](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) et spécifier une plage d'IOPS pour la taille de volume que vous choisissez. Les IOPS personnalisées sont une bonne option lorsque vous avez des exigences de performances bien définies qui ne relèvent pas d'un niveau d'IOPS prédéfini. 

## Quel nombre maximum d'IOPS puis-je attendre pour mes volumes de données ? 
{: faq}

Le nombre maximum d'IOPS pour les volumes de données varie en fonction de la taille du volume et du profil de niveau d'IOPS que vous avez sélectionné. Par exemple, le nombre maximal d’IOPS pour un volume à usage général jusqu'à 1 To est de 3 000 IOPS. Pour plus d'informations, voir [ Profils IOP hiérarchisés](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). Si vous choisissez un [profil IOPS personnalisé](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom), définissez également une plage minimale et maximale pour une taille de volume donnée. 

## Que se passe-t-il si j'utilise une taille de bloc plus petite lors de la mesure des performances ? 
{: faq}

Le nombre maximal d'IOPS peut toujours être obtenu en utilisant des tailles de bloc inférieures, mais le débit sera moindre. Par exemple, un volume doté de 6 000 IOPS présente les débits suivants en fonction des tailles de bloc :

* 16 ko * 6 000 IOPS == ~93,75 Mo/sec
* 8 ko * 6 000 IOPS == ~46,88 Mo/sec
* 4 ko * 6 000 IOPS == ~23,44 Mo/sec

## Dois-je payer pour l'utilisation et existe-t-il des limites de quota ? 
{: faq}

Pour plus d'informations sur la facturation, voir [Tarification du service Block Storage for VPC](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing). Certaines limites s'appliquent. Pour plus d'informations sur les quotas et les limites de votre instance {{site.data.keyword.cloud}} Cloud Virtual Private Cloud et sur les ressources disponibles qu'elle contient, consultez la rubrique [Quotas](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas). 

## Après avoir créé un volume, puis-je augmenter sa capacité ultérieurement ? 
{: faq}

Non, vous ne pouvez pas augmenter la capacité d'un volume. Nous vous recommandons d'estimer une capacité suffisante pour la croissance projetée avant de mettre à disposition un volume de stockage par blocs. 

## Le volume doit-il être préchauffé pour obtenir le débit prévu ?
{: faq}

Il est inutile de préchauffer un volume. Vous pouvez voir le débit spécifié immédiatement lors de la mise à disposition du volume. 

## Puis-je créer des volumes chiffrés ? 
{: faq}

Tous les volumes de stockage par blocs sont chiffrés, soit par le chiffrement géré par IBM (par défaut), soit via le service Key Protect à l'aide de vos propres clés de chiffrement. Pour plus d'informations, voir [Création de volumes de stockage par blocs avec un chiffrement géré par le client](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

## Comment déterminer le type de chiffrement d'un volume ? 
{: faq}

Dans l'interface utilisateur, lorsque vous consultez la liste de tous les volumes de stockage par blocs, la colonne Chiffrement indique si le chiffrement est géré par le fournisseur ou par le client. 

Pour afficher les propriétés d'un volume à partir de la CLI, entrez : 

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## Quel est le niveau de sécurité de mes données ? 
{: faq}

Tous les volumes de stockage par blocs sont chiffrés au repos par le chiffrement géré par IBM ou à l'aide de vos propres clés de chiffrement. Les clés gérées par IBM sont générées et stockées en toute sécurité dans un coffre de stockage par blocs à l'aide de Consul, puis gérées par le système. Les clés gérées par le client sont gérées en toute sécurité à l'aide du service IBM Key Protect. 

## Que dois-je faire à propos des sauvegardes de données pour la reprise après incident ? 
{: faq}

Block Storage for VPC sécurise vos données dans des zones de défaillance redondantes de votre région. Nous vous encourageons également à sauvegarder vos données sur un support indépendant. Vous pouvez également envisager d'utiliser [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started), qui fournit des fonctionnalités de reprise après incident telles que le clonage de volumes, les instantanés et la réplication. 

## Combien de volumes puis-je mettre à disposition ?
{: faq}

Vous pouvez mettre à disposition jusqu'à 1 000 volumes de stockage par blocs par région. 

## Quelle stratégie dois-je utiliser pour gérer mes volumes ? 
{: faq}

Déterminez la capacité dont vous avez besoin en fonction de la croissance prévue. Vous ne pouvez pas augmenter la taille des volumes après la mise à disposition. Cependant, vous pouvez créer autant de volumes que nécessaire. De même, si vous avez des exigences de performances bien définies, vous pouvez envisager de choisir des [IOPS personnalisées](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) offrant une plage spécifique d'IOPS par taille de volume. 

## Comment le disque d'amorçage d'une instance de serveur virtuel est-il créé et quel est son rapport avec le fichier image ? 
{: faq}

Le disque d'amorçage, également appelé volume d'amorçage, est créé lorsque vous mettez à disposition une instance de serveur virtuel Le disque d'amorçage d'une instance est une image clonée de l'image de la machine virtuelle. Le volume d'amorçage est supprimé lorsque vous supprimez l'instance à laquelle il est connecté. 

## Les pare-feux ou les groupes de sécurité ont-ils un impact sur les performances ? 
{: faq}

Les bonnes pratiques recommandent d'exécuter le trafic de stockage sur un VLAN qui contourne le pare-feu. L'exécution du trafic de stockage via des pare-feux logiciels augmente le temps d'attente et a un impact négatif sur les performances de stockage.

## Quand puis-je supprimer un volume de données de stockage par blocs ? 
{: faq}

Vous pouvez supprimer un volume de données de stockage par blocs uniquement s'il n'est pas connecté à une instance de serveur virtuel. [Déconnectez le volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach) avant de le supprimer. Les volumes d'amorçage sont déconnectés et supprimés lorsque l'instance est supprimée. 

## Qu'advient-il de mes données lorsque je supprime un volume de données de stockage par blocs ? 
{: faq}

Lorsque vous supprimez un volume de données de stockage par blocs, tous les pointeurs vers les données de ce volume sont supprimés et les données deviennent complètement inaccessibles. Si vous remettez à disposition ultérieurement le stockage physique sur un autre compte, un nouvel ensemble de pointeurs est attribué. Il n’existe aucun moyen pour ce nouveau compte d’accéder aux données qui se trouvaient éventuellement sur le stockage physique ; le nouvel ensemble de pointeurs indique uniquement des 0. Lorsque de nouvelles données sont écrites sur le volume, toutes les données inaccessibles sont écrasées. 

## Quels temps d'attente de performance puis-je attendre de mon stockage par blocs ? 
{: faq}

Le temps d'attente cible dans le stockage est inférieur à 1 milliseconde. Le stockage par blocs est connecté à des instances de calcul sur un réseau partagé. Le temps d'attente exact des performances dépend donc du trafic réseau dans une période donnée. 

## Puis-je configurer un stockage partagé dans un cluster multizone ? 
{: faq}

Dans IBM Cloud, les options de stockage sont localisées dans une zone de disponibilité. Nous ne recommandons pas de gérer le stockage partagé sur plusieurs zones. 

Au lieu de cela, utilisez une option de service classique de données IBM Cloud telle qu'{{site.data.keyword.cos_full}} ou {{site.data.keyword.cloudantfull}}, si vous devez partager vos données sur plusieurs zones et régions. 

## J'ai des volumes sur l'infrastructure classique. Puis-je les transférer sur le VPC ? 
{: faq}

Non. Le VPC donne accès à de nouvelles zones de disponibilité dans les régions multizones. Les ressources de calcul, de réseau et de stockage sont spécialement conçues pour fonctionner dans le VPC. 
