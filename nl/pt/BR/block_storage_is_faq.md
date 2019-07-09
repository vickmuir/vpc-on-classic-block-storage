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

# Perguntas mais frequentes do armazenamento de bloco para VPC
{: #block-storage-vpc-faq}

## Como alocar armazenamento para minhas instâncias?
{: faq}

Quando você cria uma instância de servidor virtual, é possível [criar um volume de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi) que será anexado a essa instância. Também é possível [criar volumes independentes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol) e, posteriormente, anexá-los às suas instâncias.

## Quantas instâncias podem compartilhar um volume de armazenamento de bloco provisionado?
{: faq}

Um volume de armazenamento de bloco pode ser anexado apenas a uma instância de cada vez. As instâncias não podem compartilhar o mesmo volume.

## Quantos volumes secundários de armazenamento de bloco (dados) podem ser anexados a uma instância?
{: faq}

Instâncias com menos de 4 vCPUs podem conectar até 4 volumes secundários de armazenamento de bloco.

Instâncias com 4 vCPUs ou mais podem anexar até 12 volumes secundários de armazenamento de bloco.

## Ao provisionar IOPs, o IOPS alocado é impingido por instância ou por volume?
{: faq}

O IOPS é cumprido no nível de volume.

## Como o IOPS é medido?
{: faq}

As IOPS são medidas com base em um perfil de carregamento de blocos de 16 KB com 50% de leitura
e 50% de gravações aleatórias. As cargas de trabalho que diferem desse perfil podem ter um desempenho inferior.

## O que são perfis IOPS?
{: faq}

Os perfis IOPS definem o desempenho de IOPS/GB para volumes de várias capacidades. Há três [camadas de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) predefinidas que é possível selecionar que oferecem desempenho de IOPS garantido para atender aos requisitos de carga de trabalho. Também é possível definir [IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e especificar um intervalo de IOPS para um tamanho de volume escolhido. O IOPS customizado é uma boa opção quando você tem requisitos de desempenho bem definidos que não se enquadram em uma camada de IOPS predefinida.

## Quais são os IOPS máximos que posso esperar para meus volumes de dados?
{: faq}

Os IOPS máximos para volumes de dados variam com base no tamanho do volume e no perfil da camada IOPS selecionado. Por exemplo, o máximo de IOPS para um volume de propósito geral de até 1 TB é 3.000 IOPS. Para obter informações, consulte [Perfis de IOPs em Camadas](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). Se você escolher um [Perfil de IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom), defina também um intervalo mínimo e máximo para um determinado tamanho de volume.

## O que acontece se eu usar um tamanho de bloco menor ao medir o desempenho?
{: faq}

O máximo de IOPS ainda pode ser obtido ao usar tamanhos de blocos menores, porém o rendimento será inferior. Por exemplo, um volume com 6.000 IOPS teria o rendimento a seguir em vários tamanhos de bloco:

* 16 KB * 6.000 IOPS == ~93,75 MB/s
* 8 KB * 6.000 IOPS == ~46,88 MB/s
* 4 KB * 6.000 IOPS == ~23,44 MB/s

## Eu serei cobrado pelo uso e há limites de cota?
{: faq}

Para obter mais informações sobre como você é o faturamento, consulte [Precificação do armazenamento de bloco para VPC](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing). Determinados limites se aplicam.
Para obter mais informações sobre cotas e limites para o seu {{site.data.keyword.cloud}} Virtual Private Cloud e os recursos disponíveis nele, consulte [Cotas](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas).

## Depois de criar um volume, posso aumentar sua capacidade mais tarde?
{: faq}

Não, não é possível aumentar a capacidade de um volume. Recomendamos que você estime a capacidade suficiente para o crescimento projetado antes de provisionar um volume de armazenamento de bloco.

## O volume precisa ser pré-aquecido para alcançar o rendimento esperado?
{: faq}

Você não tem que pré-aquecer um volume. É possível ver o rendimento especificado imediatamente após o fornecimento do volume.

## Posso criar volumes criptografados?
{: faq}

Todos os volumes de armazenamento de bloco são criptografados, pela criptografia gerenciada pela IBM (padrão) ou por meio do serviço Key Protect usando suas próprias chaves de criptografia. Para obter informações, consulte [Criando volumes de armazenamento de bloco com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

## Como posso dizer o tipo de criptografia que um volume possui?
{: faq}

Na UI, quando você visualiza sua lista de todos os volumes de armazenamento de bloco, a coluna Criptografia indica a criptografia gerenciada pelo provedor ou pelo cliente.

Para mostrar as propriedades de um volume pela CLI, insira:

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## Quão protegidos são meus dados?
{: faq}

Todos os volumes de armazenamento de bloco são criptografados em repouso pela criptografia gerenciada pela IBM ou usando suas próprias chaves de criptografia. As chaves gerenciadas pela IBM são geradas e armazenadas com segurança em uma área segura de armazenamento de bloco, apoiada pelo Consul e, em seguida, mantida pelo sistema. As chaves gerenciadas pelo cliente são gerenciadas com segurança usando o serviço IBM Key Protect.

## O que devo fazer sobre os backups de dados para recuperação de desastre?
{: faq}

O Armazenamento de bloco para VPC protege seus dados entre zonas de falha redundantes em sua região. Também encorajamos você a fazer backup de seus dados de forma independente. Também é possível considerar o uso do [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started), que fornece recursos de recuperação de desastre, como clonagem de volume, capturas instantâneas e replicação.

## Quantos volumes posso provisionar?
{: faq}

É possível provisionar até 1.000 volumes de armazenamento de bloco por região.

## Qual estratégia devo usar para gerenciar meus volumes?
{: faq}

Determine a capacidade que você precisa com base no crescimento previsto. O tamanho do volume não pode ser expandido após o fornecimento. No entanto, é possível criar novos volumes, conforme necessário. Além disso, se você tiver requisitos de desempenho bem definidos, será possível considerar a escolha de [IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) que fornece um intervalo específico de IOPS por tamanho do volume.

## Como o disco de inicialização é criado para uma instância de servidor virtual e como ele se relaciona com o arquivo de imagem?
{: faq}

O disco de inicialização, também chamado de volume de inicialização, é criado quando você provisiona uma instância de servidor virtual. O disco de inicialização de uma instância é uma imagem clonada da imagem da máquina virtual. O volume de inicialização é excluído quando você exclui a instância à qual ele está anexado.

## Os firewalls ou os grupos de segurança afetam o desempenho?
{: faq}

Como melhor prática, é recomendável executar o tráfego de armazenamento em uma VLAN que efetua bypass do firewall. A execução do tráfego de armazenamento por meio de firewalls de software aumenta a latência e afeta negativamente o desempenho do armazenamento.

## Quando posso excluir um volume de dados de armazenamento de bloco?
{: faq}

É possível excluir um volume de dados de armazenamento de bloco somente quando ele não está anexado a uma instância de servidor virtual. [Remova o volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach) antes de excluí-lo. Os volumes de inicialização são removidos e excluídos quando a instância é excluída.

## O que acontece com meus dados quando eu excluo um volume de dados de armazenamento de bloco?
{: faq}

Quando você exclui um volume de dados de armazenamento de bloco, todos os ponteiros para os dados nesse volume são removidos e os dados ficam completamente inacessíveis. Se você reprovisionar posteriormente o armazenamento físico para outra conta, um novo conjunto de ponteiros será designado. Não há nenhuma maneira de essa nova conta acessar quaisquer dados que possam ter estado no armazenamento físico; o novo conjunto de ponteiros mostra todos os 0's. Quando novos dados são gravados no volume, quaisquer dados inacessíveis são sobrescritos.

## Qual latência de desempenho posso esperar do meu armazenamento de bloco?
{: faq}

A latência de destino dentro do armazenamento é menor que 1 milissegundo. O armazenamento de bloco está conectado às instâncias de cálculo em uma rede compartilhada, portanto, a latência exata de desempenho dependerá do tráfego de rede dentro de um determinado intervalo de tempo.

## Posso configurar o armazenamento compartilhado em um cluster multizona?
{: faq}

No IBM Cloud, as opções de armazenamento estão localizadas em uma zona de disponibilidade. Não recomendamos o gerenciamento do armazenamento compartilhado em múltiplas zonas.

Em vez disso, use uma opção de serviço clássico de dados do IBM Cloud, como {{site.data.keyword.cos_full}} ou {{site.data.keyword.cloudantfull}}, se você precisar compartilhar seus dados entre múltiplas zonas e regiões.

## Eu tenho volumes na infraestrutura Classic. Posso portá-los para o VPC?
{: faq}

Não.  O VPC fornece acesso a novas zonas de disponibilidade em regiões de várias zonas. Os recursos de cálculo, rede e armazenamento são especificamente projetados para funcionar no VPC.
