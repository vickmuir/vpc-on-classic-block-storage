---

copyright:
  years: 2019
lastupdated: "2019-06-14"

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

# Capacidade e desempenho do Armazenamento de bloco
{: #capacity-performance}

É importante escolher o tamanho do volume de armazenamento de bloco ideal e o nível de desempenho para suas cargas de trabalho. Ao provisionar o armazenamento de bloco por meio da UI ou da CLI, é possível escolher o tamanho de seu volume e o nível de desempenho.

### Capacidade
{: #block-storage-vpc-capacity}

É possível especificar 10 GB a 2000 GB (2 TB) de capacidade por volume de dados de armazenamento de bloco em incrementos de 1 GB. A capacidade total do volume é determinada quando você seleciona um [perfil de IOPS](#iops-profiles). Os volumes de inicialização são de 100 GB.

### Perfis de IOPS
{: #iops-profiles}

Ao provisionar volumes de {{site.data.keyword.block_storage_is_short}}, você especifica um [perfil de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) que melhor atende aos seus requisitos de armazenamento. Os perfis estão disponíveis como três camadas IOPS predefinidas ou como IOPS customizado. As [camadas de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornecem desempenho de IOPS/GB garantido para volumes de até 2 TB de capacidade. Também é possível especificar um perfil de [IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e definir a capacidade de volume e o IOPS dentro de um intervalo. Use o console do {{site.data.keyword.cloud_notm}}, a CLI ou a API para especificar um perfil.

## Como o tamanho de bloco afeta o desempenho
{: #how-block-size-affects-performance}

O IOPS é baseado em um tamanho de bloco de 16 KB com uma carga de trabalho aleatória de 50% de leitura/gravação 50/50. Um bloco de 16 KB equivale a uma gravação no
volume. O rendimento da linha de base é determinado pela quantidade de IOPS multiplicada pelo tamanho de bloco de 16 KB. Quanto mais alto o IOPS você especificar, maior será o rendimento. O rendimento máximo para um volume de armazenamento de bloco é 750 MB/s.

O tamanho de bloco escolhido para seu aplicativo impacta diretamente o desempenho do armazenamento. Se o tamanho do bloco for menor que 16 KB, o limite de IOPS será atingido antes do limite de rendimento. Por outro lado, se o tamanho do bloco for maior que 16 KB, o limite de rendimento será atingido antes do limite de IOPS. A tabela a seguir fornece alguns exemplos de como o tamanho de bloco e o IOPS afetam o rendimento.

| Tamanho de bloco (KB) | IOPS | Rendimento (MB/s) |
|-----------------|------|-------------------|
| 4 (típico para Linux) | 1.000 | 4 |
| 8 (típico para Oracle) | 1.000  | 8 |
| 16 | 1.000 | 16 |
| 32 (típico para o SQL Server) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="A Tabela 1 mostra exemplos de como o tamanho do bloco e o IOPS afetam o rendimento.<br/>Tamanho médio de IO x IOPS = rendimento em MB/s." caption-side="top"}
