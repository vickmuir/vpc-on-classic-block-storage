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

# Sobre o armazenamento de bloco para VPC
{: #block-storage-about}
[comment]: # (tópico da ajuda vinculado)

O {{site.data.keyword.block_storage_is_full}} (VPC) fornece armazenamento de dados montado pelo hypervisor de alto desempenho para as instâncias do servidor virtual (instâncias) que você pode provisionar em um {{site.data.keyword.vpc_full}} (VPC). A infraestrutura do VPC fornece escalabilidade rápida em múltiplas regiões e zonas, além de desempenho e segurança extras. Para obter mais informações sobre o {{site.data.keyword.vpc_short}}, consulte [Sobre a Nuvem particular virtual](/docs/vpc-on-classic?topic=vpc-on-classic-about).
{:shortdesc}

O {{site.data.keyword.block_storage_is_short}} fornece volumes de inicialização primários e volumes de dados secundários. Os volumes de inicialização são criados e anexados automaticamente durante o fornecimento da instância. Os volumes de dados podem ser criados e anexados durante o fornecimento da instância também ou como volumes independentes que podem ser anexados posteriormente a uma instância. Para proteger seus dados, é possível usar sua própria chave de criptografia ou escolher criptografia gerenciada pela IBM. Os [perfis da camada de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) permitem que você especifique um nível predefinido de desempenho para seus volumes. Ou, é possível escolher um [perfil de IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e definir sua própria capacidade de volume e nível de IOPS.

## Armazenamento de bloco para volumes VPC
{: #block-storage-vpc-volumes}

O {{site.data.keyword.block_storage_is_short}} oferece volumes de armazenamento de dados de nível de bloco que podem ser anexados a uma instância como volume de inicialização ou como volume de dados. É possível configurar até 750 volumes de armazenamento de bloco por região. É possível anexar vários volumes de dados de armazenamento de bloco a uma única instância para capacidade extra. O número de volumes que podem ser anexados a uma instância depende de quantas vCPUs essa instância contém. Para obter mais informações, consulte [Limites de anexo de volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits).

### Volumes de inicialização
{: #block-storage-vpc-boot-volumes}

Quando você cria uma instância, um volume de inicialização de 100 GB é automaticamente criado e anexado à instância. O volume de inicialização tem um número máximo de 3.000 IOPS. É possível criptografar o volume de inicialização usando [suas próprias chaves de criptografia](#about-customer-managed-encrytion) ou usar a [criptografia gerenciada pelo provedor](#about-provider-managed-encryption) padrão. Um volume de inicialização não pode ser removido manualmente e excluído, mas ele é excluído quando você exclui a instância.

### Volumes de dados secundários
{: #secondary-data-volumes}

Os volumes de dados de armazenamento de bloco são volumes secundários com intervalo de capacidade total de 10 GB a 2000 GB. O máximo de IOPS para volumes de dados varia com base no tamanho do volume e no perfil da camada de IOPS selecionado. Por exemplo, o máximo de IOPS para um volume de propósito geral de até 1 TB é 3.000 IOPS. Para obter mais informações, consulte [Perfis de IOPS em camadas](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers).

Crie volumes de dados como volumes independentes ou quando você provisionar uma instância. Os volumes independentes existem em um estado não anexado até que você anexe o volume a uma instância. Ao criar um volume de dados como parte do fornecimento da instância, o volume é anexado automaticamente à instância.  

Os volumes de dados de armazenamento de bloco podem ser anexados a qualquer instância disponível dentro de sua região, dentro de [determinados limites](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits). Esses volumes são removidos por padrão quando a instância é excluída. A remoção por padrão permite que seus dados persistam além do ciclo de vida da instância do servidor virtual. Ela remove somente a associação do volume com a instância. É possível excluir volumes de dados manualmente após eles serem removidos ou, ao criar um volume, é possível especificar que ele seja [removido e excluído automaticamente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete) quando a instância for excluída.

Os volumes de dados são criptografados por padrão com a criptografia gerenciada pela IBM. Como opção, é possível criptografar volumes de dados usando [sua própria chave de criptografia](#about-customer-managed-encrytion).

## Criptografia para dados em repouso
{: #encryption}

O {{site.data.keyword.cloud_notm}} leva a sério a necessidade de segurança e entende a importância de ser capaz de criptografar dados para mantê-los seguros. Quando você cria um volume independente ou cria um volume como parte da criação da instância, é possível escolher proteger seus dados com a criptografia gerenciada por provedor IBM ou usar suas próprias chaves de criptografia.  

### Criptografia gerenciada por provedor
{: #about-provider-managed-encryption}

Por padrão, todos os volumes de inicialização e dados são criptografados com a criptografia gerenciada pelo provedor IBM. Não há nenhum custo adicional para esse serviço ou impacto no desempenho. A criptografia gerenciada por provedor usa os protocolos padrão de mercado a seguir:

* Criptografia AES-256
* As chaves são gerenciadas internamente com o Key Management Interoperability Protocol (KMIP)
* O armazenamento é validado para o Federal Information Processing Standard (FIPS) Publication 140-2, o Federal Information Security Management Act (FISMA) e o Health Insurance Portability and Accountability Act (HIPAA). O armazenamento também é validado para o Payment Card Industry (PCI), o Basel II, o Security Breach Information Act (SB 1386) da Califórnia e a conformidade com a Data Protection Directive 95/46/EC da União Europeia.

### Criptografia gerenciada pelo cliente
{: #about-customer-managed-encrytion}

É possível criptografar volumes de armazenamento de bloco com suas próprias chaves de criptografia. Para volumes de dados, você especifica a criptografia gerenciada pelo cliente ao criar o volume. Para volumes de inicialização, é possível editar as propriedades do volume de inicialização durante a criação da instância e especificar a criptografia gerenciada pelo cliente. Para obter os procedimentos, consulte [Criando volumes de armazenamento de bloco com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Com a criptografia gerenciada pelo cliente, sua chave de criptografia é transferida por upload para um serviço de gerenciamento de chave ({{site.data.keyword.keymanagementservicelong_notm}} ou {{site.data.keyword.hscrypto}}). A infraestrutura VPC localiza a chave na instância de serviço de gerenciamento de chave que você configurou antecipadamente e, em seguida, criptografa o volume. Para obter os pré-requisitos e um procedimento de configuração única, consulte [Criando volumes de armazenamento de bloco com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Para obter mais informações sobre a criação da criptografia gerenciada pelo cliente para volumes durante o fornecimento da instância de servidor virtual, consulte [Criptografia gerenciada pelo cliente para armazenamento de bloco](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys).

## Informações relacionadas

Para obter mais informações sobre a criação e o gerenciamento de instâncias no VPC, consulte [Sobre servidores virtuais para VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

Para começar a criar armazenamento de bloco para VPC, consulte [Criando volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage).

O {{site.data.keyword.block_storage_is_short}} fornece recursos exclusivos para o VPC e não é compatível com o armazenamento de infraestrutura clássica. Se você estiver interessado em {{site.data.keyword.blockstoragefull}} na infraestrutura clássica, consulte [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).
{:note}
