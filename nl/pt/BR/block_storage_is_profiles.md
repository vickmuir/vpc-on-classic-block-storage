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

# Perfis do {{site.data.keyword.block_storage_is_short}}
{: #block-storage-profiles}

Quando você provisiona volumes secundários do {{site.data.keyword.block_storage_is_short}} usando o console, a CLI ou a API do {{site.data.keyword.cloud_notm}}, você especifica um perfil IOPS que melhor atende aos seus requisitos de armazenamento. Os perfis estão disponíveis como três camadas IOPS predefinidas ou como IOPS customizado.  As camadas de IOPS fornecem desempenho de IOPS/GB garantido para volumes de até 2 TB de capacidade. Também é possível especificar um perfil de IOPS customizado e definir a capacidade de volume e o IOPS dentro de um intervalo.
{:shortdesc}

## Perfis de IOPs em camadas
{: #tiers}

O armazenamento de bloco fornece três camadas de IOPS predefinidos que é possível selecionar para especificar o desempenho ideal para suas cargas de trabalho de cálculo e para evitar gargalos. É possível fornecer volumes em sua zona de disponibilidade com IOPS garantido, conforme descrito na tabela a seguir:

| Camada de IOPS | Carga de trabalho | Tamanho do volume | Máximo de IOPS |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | Cargas de trabalho de propósito geral - Cargas de trabalho que hospedam bancos de dados pequenos para aplicativos da web ou armazenam imagens de disco da máquina virtual para um hypervisor | 10 GB a 1 TB | Até 3.000 IOPS |
| | | Acima de 1 TB a 2 TB | 3 IOPS/GB de até 6.000 IOPS |
| 5 IOPS/GB | Cargas de trabalho de intensidade de E/S alta - Cargas de trabalho caracterizadas por uma grande porcentagem de dados ativos, como bancos de dados transacionais e outros sensíveis ao desempenho| 10 GB a 600 GB | Até 3.000 IOPS |
| | | Acima de 600 GB a 2 TB | 5 IOPS/GB de até 10.000 IOPS|
| 10 IOPS/GB | Cargas de trabalho de armazenamento exigentes - Cargas de trabalho com intenso uso de dados criadas por bancos de dados NoSQL, processamento de dados para vídeo, aprendizado de máquina e analítica | 10 GB a 300 GB | Até 3.000 IOPS |
| | | Acima de 300 GB a 2 TB | 10 IOPS/GB de até 20.000 IOPS |
{: caption="Tabela 1. Perfis de camada do IOPS e níveis de desempenho para cada camada" caption-side="top"}

O rendimento máximo de todas as camadas de IOPS de armazenamento de bloco é de 750 MB/s com base em um tamanho de bloco de 16K

## Perfil de IOPS customizado
{: #custom}

O IOPS customizado é uma boa opção quando você tem requisitos de desempenho bem definidos que não se enquadram em uma camada de IOPS predefinida. É possível customizar o IOPS especificando o IOPS total para o volume dentro do intervalo para seu tamanho de volume. É possível fornecer volumes com 100 IOPS para 20.000 IOPS.

A tabela a seguir mostra os intervalos de IOPS disponíveis com base no tamanho do volume.

| Tamanho do volume (GB) | Intervalo de IOPS |
|-------------|--------------|
| 10 a 39   | 100 a 1.000 |
| 40 a 79 | 100 a 2.000 |
| 80 a 99 | 100 a 4.000 |
| 100 a 499 | 100 a 6.000 |
| 500 a 999 | 100 a 10.000 |
| 1.000 a 1.999 | 100 a 20.000 |
{: caption="Tabela 2. IOPS disponível com base no tamanho do volume" caption-side="top"}

## Como os perfis de servidor virtual se relacionam aos perfis de armazenamento
{: #vsi-profiles-relate-to-storage}

Perfis de servidor virtual são uma combinação de vCPU e RAM que podem ser instanciados rapidamente para iniciar uma instância de servidor virtual.  Você seleciona entre [três famílias de perfis](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles)
com base em seus requisitos de carga de trabalho.  Esses requisitos podem variar de cargas de trabalho comuns a cargas de trabalho com uso intenso de CPU ou memória.  

Da mesma forma, os perfis de armazenamento (camadas de IOPS ou customizado) fornecem um intervalo de capacidade e desempenho para volumes secundários.  Por padrão,
um volume de inicialização primário de 100 GB é criado quando você cria uma instância de servidor virtual.  Também é possível criar e anexar volumes secundários.  
Ao criar um volume de dados secundário como parte da criação da instância, você seleciona um perfil de armazenamento que melhor atenda aos seus
requisitos de armazenamento para suas cargas de trabalho de cálculo. Em geral, à medida que seus requisitos de cálculo aumentam, é necessário um desempenho mais alto de IOPS.  A tabela a seguir mostra esse relacionamento.

| Perfil de armazenamento da camada de IOPS | Perfil do servidor virtual |
|-----------------|------------------------|
| 3 IOPS/GB       | [Balanceado](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) para cargas de trabalho comuns |
| 5 IOPS/GB       | [Cálculo](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) para demandas intensivas de CPU |
| 10 IOPS/GB      | [Memória](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) para cargas de trabalho de uso intenso de memória |
{: caption="Tabela 3. Relacionamento de perfis de armazenamento de bloco com perfis de servidor virtual" caption-side="top"}

## Visualizando perfis de IOPS
{: #view-iops-profiles}

É possível visualizar os perfis de IOPS disponíveis no console do {{site.data.keyword.cloud_notm}}, CLI ou API.

### Usando o console do IBM Cloud
{: using-console-iops-profile}

 Quando você [criar um volume de armazenamento de bloco no console do {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), selecione **Camadas** no menu suspenso.

 Como alternativa, selecione **Customizado** e, em seguida, selecione um valor de IOPS dentro do intervalo para esse tamanho de volume. Clique no link tamanho do armazenamento para ver uma tabela de intervalos de tamanho e IOPS.

 ### Usando a CLI
 {: using-cli-iops-profiles}

 Para visualizar a lista de perfis disponíveis usando a CLI, execute o comando a seguir:
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### Usando a API
{: using-api-iops-profiles}

A solicitação da API cURL a seguir recupera todos os perfis de volume.

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## Informações Relacionadas

Para obter informações sobre perfis Balanceado, Cálculo e Memória para o {{site.data.keyword.vsi_is_short}}, consulte [Perfis](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).
