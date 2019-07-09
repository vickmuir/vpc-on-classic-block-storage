---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Visualizando detalhes do volume de armazenamento de bloco
{: #viewing-block-storage}

Visualize detalhes sobre um volume de armazenamento de bloco ou informações resumidas sobre todos os volumes.

## Visualizar informações sobre todos os volumes de armazenamento de bloco
{: #viewvols}

Navegue para a lista de volumes de armazenamento de bloco. No [Console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, acesse **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Volumes de armazenamento de bloco para VPC**.

Por padrão, os volumes de armazenamento de bloco são exibidos para todos os grupos de recursos em sua região. Na lista de todos os **Volumes de armazenamento de bloco**, você verá as informações a seguir.

| Campo | Descrição |
|-------|-------------|
| Status | Status do volume, que funciona como o filtro padrão para todas as linhas. Para obter informações sobre os status do volume, consulte [Status do volume do armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status). |
| Nome | Clique no nome do volume para ver detalhes do volume individual. |
| Grupo de recursos |  Grupo de recursos definido quando você configura seu VPC. Os grupos de recursos gerenciam o acesso aos recursos, mas não afetam o faturamento ou o monitoramento.|
| Localização | Zona de disponibilidade em sua região, herdada do VPC (por exemplo, Sul dos EUA 1). |
| Tamanho | Tamanho do volume especificado, em GBs. |
| Máximo de IOPS | IOPS máximo disponível no volume, definido pela camada de IOPS de propósito geral ou pelo valor de IOPS customizado que você especificou. |
| Tipo de anexo | Dados, para um volume secundário anexado a uma instância, inicializar quando anexado como volume de inicialização ou em branco para um volume não anexado. |
| Encryption | Gerenciado pelo provedor ou [gerenciado pelo cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
| Ações (...) | Clique nas reticências para exibir um menu de ações específicas do contexto que você pode executar. Por exemplo, um volume disponível não anexado teria opções de menu para anexar a uma instância ou excluir o volume. |
{: caption="Tabela 1. Detalhes sobre todos os volumes" caption-side="top"}

Por padrão, 10 volumes são mostrados na lista de todos os volumes de armazenamento de bloco. Mude esse padrão clicando na seta para baixo e aumente a lista para 20 ou 50 volumes. Use as setas no canto inferior direito para navegar para a próxima página e voltar novamente.

## Visualizar detalhes sobre um volume de armazenamento de bloco
{: #view-vol-details}

Para visualizar detalhes sobre um volume de armazenamento de bloco, navegue para a lista de todos os volumes de armazenamento de bloco e selecione um volume.  Para um único volume, você verá as informações a seguir.

| Campo | Descrição |
|-------|-------------|
| Nome  | Nome do volume que você especificou quando criou o volume. Clique no ícone de lápis para editar o nome do volume. |
| Grupo de recursos | Grupo de recursos definido quando você configura seu VPC. Os grupos de recursos gerenciam o acesso aos recursos, mas não afetam o faturamento ou o monitoramento. |
| Tipo de anexo | Dados, para um volume secundário anexado a uma instância, inicializar quando anexado como volume de inicialização ou em branco para um volume não anexado. |
| ID | ID do volume gerado pelo sistema. |
| Criado | Data gerada pelo sistema quando o volume foi criado. |
| Localização | Zona de disponibilidade em sua região. |
| Tamanho | Tamanho do volume especificado. |
| Perfil | Camada de IOPS ou perfil de IOPS customizado. |
| Máximo de IOPS | Valor máximo de IOPS para uma camada de IOPS predefinida ou o valor que você especificou para IOPS customizado. |
| Rendimento | O desempenho que um disco pode entregar, medido em Gigabits/segundo (Gbps). Com base em seu perfil de volume, o rendimento é calculado como a quantidade de IOPS * tamanho do bloco de 16K. |
| Encryption | Gerenciado pelo provedor ou gerenciado pelo cliente. |
{: caption="Tabela 1.Detalhes do volume" caption-side="top"}

Os volumes anexados a uma instância de servidor virtual são exibidos em **Instâncias anexadas** na página **Detalhes do volume**.  Também é possível [anexar um volume a uma instância](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Para um volume anexado a uma instância, também é possível navegar para informações sobre a instância e, em seguida, retornar a uma lista de todos os volumes de Armazenamento de bloco.

## Visualizar detalhes do volume de armazenamento de bloco anexado nos detalhes da instância

É possível visualizar informações sobre um volume de armazenamento de bloco anexado na página **Detalhes da instância do servidor virtual**:

1. No [Console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, acesse **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Cálculo > Instâncias de servidor virtual para VPC** e selecione uma instância.
1. Em **Volumes de armazenamento de bloco anexados**, clique no nome de um volume para acessar a página de detalhes do volume.

Você prefere visualizar volumes de armazenamento de bloco usando a CLI? Para obter informações, consulte [Visualizando volumes de armazenamento de bloco (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli).
{: tip}

## Próximas Etapas
{: #next-step-viewing-block-storage}

Crie mais volumes ou gerencie seus volumes de armazenamento de bloco existentes.

* [Criando volumes de armazenamento de bloco no console do IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gerenciando volumes de armazenamento de bloco usando a UI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
