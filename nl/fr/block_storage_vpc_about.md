---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS, HPCS, Key Protect

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# A propos de Block Storage for VPC 
{: #block-storage-about}
[comment]: # (rubrique d'aide liée)

{{site.data.keyword.block_storage_is_full}} (VPC) fournit un stockage de données hautes performances monté sur hyperviseur pour vos instances de serveur virtuel (instances) que vous pouvez mettre à disposition dans un {{site.data.keyword.vpc_full}} (VPC). L'infrastructure VPC offre une évolutivité rapide sur plusieurs régions et zones, ainsi que des performances et une sécurité accrues. Pour plus d'informations sur {{site.data.keyword.vpc_short}}, voir [A propos de Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about).
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} fournit les volumes d'amorçage principaux et les volumes de données secondaires. Les volumes d'amorçage sont automatiquement créés et attachés lors de la mise à disposition de l'instance. Des volumes de données peuvent également être créés et connectés lors de la mise à disposition d'instances, ou en tant que volumes autonomes que vous pouvez connecter ultérieurement à une instance. Pour protéger vos données, vous pouvez utiliser votre propre clé de chiffrement ou choisir le chiffrement géré par IBM. Les [profils de niveau IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) vous permettent de spécifier un niveau de performance prédéfini pour vos volumes. Vous pouvez également choisir un [profil IOPS personnalisé](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) et définir votre propre capacité de volume et votre niveau IOPS. 

## Stockage par blocs pour les volumes VPC 
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} propose des volumes de stockage de données de niveau bloc pouvant être connectés à une instance en tant que volume d'amorçage ou volume de données. Vous pouvez configurer jusqu'à 750 volumes de stockage par blocs par région. Vous pouvez connecter plusieurs volumes de données de stockage par blocs à une seule instance pour augmenter la capacité. Le nombre de volumes que vous pouvez connecter à une instance dépend du nombre d'UC virtuelles que cette instance contient. Pour plus d'informations, voir [Limites de connexion de volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits).

### Volumes d'amorçage
{: #block-storage-vpc-boot-volumes}

Lorsque vous créez une instance, un volume d'amorçage de 100 Go est automatiquement créé et connecté à l'instance. Le volume d'amorçage a un maximum de 3 000 IOPS. Vous pouvez chiffrer le volume d'amorçage à l'aide de [vos propres clés de chiffrement](#about-customer-managed-encrytion) ou utiliser le [chiffrement par défaut géré par le fournisseur](#about-provider-managed-encryption). Un volume d'amorçage ne peut pas être déconnecté et supprimé manuellement, mais il est supprimé lorsque vous supprimez l'instance. 

### Volumes de données secondaire
{: #secondary-data-volumes}

Les volumes de données de stockage par blocs sont des volumes secondaires d'une capacité totale allant de 10 Go à 2 000 Go. Le nombre maximum d'IOPS pour les volumes de données varie en fonction de la taille du volume et du profil de niveau d'IOPS que vous avez sélectionné. Par exemple, le nombre maximal d’IOPS pour un volume à usage général jusqu'à 1 To est de 3 000 IOPS. Pour plus d'informations, voir [ Profils IOP hiérarchisés](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). 

Vous créez des volumes de données en tant que volumes autonomes ou lorsque vous mettez à disposition une instance. Les volumes autonomes existent à l'état non connecté jusqu'à ce que vous le connectiez à une instance. Lorsque vous créez un volume de données dans le cadre du mise à disposition d'instance, le volume est automatiquement connecté à l'instance.   

Les volumes de données de stockage par blocs peuvent être connectés à toute instance disponible dans votre région, dans [certaines limites](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits). Ces volumes sont déconnectés par défaut lorsque l'instance est supprimée. La déconnexion par défaut permet à vos données de persister au-delà du cycle de vie de l'instance de serveur virtuel. Elle supprime uniquement l'association du volume avec l'instance. Vous pouvez supprimer les volumes de données manuellement après leur déconnexion ou, lors de la création d'un volume, vous pouvez spécifier qu'il soit [automatiquement déconnecté et supprimé](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete) lorsque l'instance est supprimée. 

Les volumes de données sont chiffrés par défaut à l'aide du chiffrement géré par IBM. Vous pouvez éventuellement chiffrer des volumes de données à l'aide de [votre propre clé de chiffrement](#about-customer-managed-encrytion). 

## Chiffrement des données au repos
{: #encryption}

{{site.data.keyword.cloud_notm}} prend les exigences de sécurité très au sérieux et comprend l'importance de pouvoir chiffrer les données pour les protéger. Lorsque vous créez un volume autonome ou un volume dans le cadre de la création d'instance, vous pouvez choisir de sécuriser vos données à l'aide du chiffrement géré par le fournisseur IBM ou d'utiliser vos propres clés de chiffrement.   

### Chiffrement géré par le fournisseur 
{: #about-provider-managed-encryption}

Par défaut, tous les volumes d'amorçage et de données sont chiffrés à l'aide du chiffrement géré par le fournisseur IBM. Il n'y a aucun coût supplémentaire pour ce service ni impact sur les performances. Le chiffrement géré par le fournisseur utilise les protocoles standard suivants : 

* Chiffrement AES-256 
* Les clés sont gérées en interne à l'aide du protocole KMIP (Key Management Interoperability Protocol) 
* Le stockage est validé pour la norme FIPS (Federal Information Processing Standard) Publication 140-2, la loi Federal Information Security Management Act (FISMA) et la loi Health Insurance Portability and Accountability Act (HIPAA). Il est également validé pour la norme PCI (Payment Card Industry), Bâle II, la loi California Security Breach Information Act (SB 1386) et la directive européenne relative à la protection des données 95/46/EC.

### Chiffrement géré par le client
{: #about-customer-managed-encrytion}

Vous pouvez chiffrer des volumes de stockage par blocs avec vos propres clés de chiffrement. Pour les volumes de données, vous spécifiez le chiffrement géré par le client lors de la création du volume. Pour les volumes d'amorçage, vous pouvez modifier les propriétés du volume d'amorçage lors de la création de l'instance et spécifier le chiffrement géré par le client. Pour connaître les procédures, voir [Création de volumes de stockage par blocs avec un chiffrement géré par le client](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Avec le chiffrement géré par le client, votre clé de chiffrement est téléchargée vers un service de gestion de clés ({{site.data.keyword.keymanagementservicelong_notm}} ou {{site.data.keyword.hscrypto}}). L'infrastructure VPC localise la clé dans l'instance de service de gestion de clés que vous avez configurée à l'avance, puis chiffre le volume. Pour connaître les conditions préalables et une procédure de configuration unique, voir [Création de volumes de stockage par blocs avec un chiffrement géré par le client](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Pour plus d'informations sur la création d'un chiffrement géré par le client pour les volumes lors de la mise à disposition d'instance de serveur virtuel, voir [Chiffrement géré par le client pour le stockage par blocs](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys). 

## Informations connexes

Pour plus d'informations sur la création et la gestion d'instances dans le VPC, voir [A propos de Virtual Servers for VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

Pour commencer à créer un stockage par blocs pour VPC, voir [Création de volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage).

{{site.data.keyword.block_storage_is_short}} fournit des fonctionnalités uniques au VPC et n'est pas compatible avec le stockage d'infrastructure classique. Si vous êtes intéressé par {{site.data.keyword.blockstoragefull}} sur l'infrastructure classique, voir [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).
{:note}
