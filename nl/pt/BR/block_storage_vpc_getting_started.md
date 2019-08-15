---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, getting started, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

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
{:shortdesc: .shortdesc}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Introdução ao {{site.data.keyword.block_storage_is_short}}
{: #getting-started}

Este tutorial ajuda a iniciar a criação de volumes de {{site.data.keyword.block_storage_is_short}} em uma Nuvem particular virtual.
{: .shortdesc}

## Antes
de Começar
{: #block-storage-before-you-begin}

Para iniciar, primeiro revise o conteúdo que pode ajudar com sua implementação. Você é novo no {{site.data.keyword.cloud}} e no {{site.data.keyword.block_storage_is_short}}? As informações a seguir podem ajudar:

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [Sobre o armazenamento de bloco para VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

Inscreva-se para uma conta do {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Assinando o {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}.

## Etapa 1 - Determine os requisitos de armazenamento
{: #determine-storage-requirements}

Você está executando cargas de trabalho de propósito geral com requisitos de armazenamento modestos? Ou, suas cargas de trabalho estão com uso intenso de E/S que requerem maior capacidade e desempenho? Para saber mais sobre como é possível determinar a capacidade e o desempenho, consulte [Capacidade do armazenamento de bloco e desempenho](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance). Além disso, consulte [Perfis](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) para saber qual opção de perfil de IOPS pode melhor atender aos seus requisitos de armazenamento. 

Você está criando uma instância de servidor virtual também? Consulte [como os perfis de servidor virtual estão relacionados a perfis de armazenamento](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage).

## Etapa 2 - Tamanho e preço de seu armazenamento de bloco
{: #size-price-block-storage}

Selecione um [perfil da camada de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) para seu volume de armazenamento de bloco.  Como opção, se você tiver requisitos de desempenho bem definidos que não estão dentro de uma camada de IOPS predefinida, escolha um [perfil de IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). 

Depois de escolher o tamanho e o desempenho para seus volumes de armazenamento de bloco, consulte as informações de [Precificação](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing) para ajudar a precificar seus volumes e entender como é o faturamento.

## Etapa 3 - Efetue login em sua conta do {{site.data.keyword.cloud_notm}}
{: block-storage-log-into-ibm-account}

Acesse o formulário de pedido do {{site.data.keyword.block_storage_is_short}} no [catálogo do {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: external}. Use seu IBMid e senha.

## Etapa 4 (opcional) - Verifique o acesso ao {{site.data.keyword.vpc_short}}

Se você deseja criar um volume dentro de uma Nuvem privada virtual, deve-se primeiro [criar um VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console). Ignore esta etapa se você desejar criar um volume independente fora do VPC. É possível solicitar posteriormente acesso ao {{site.data.keyword.vpc_short}} para acessar uma instância e anexar um volume de armazenamento de bloco que você criou independentemente. Para obter mais informações sobre o {{site.data.keyword.vpc_short}}, consulte o [Tutorial de introdução do VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Etapa 5 - Criar volumes de armazenamento de bloco

Comece a criar seus volumes no [console do {{site.data.keyword.cloud_notm}} (UI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage) ou usando a [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) ou a [API do {{site.data.keyword.vpc_short}}](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}. Para obter mais informações sobre como usar as ferramentas do IBM Cloud Developer para instalar a CLI do IBM Cloud, consulte [Introdução às ferramentas do IBM Cloud Developer](/docs/cli?topic=cloud-cli-getting-started).

## Próximas Etapas
{: #next-step-block-storage-getting-started}

Depois de criar o armazenamento de bloco, explore mais opções:

* [Visualizar detalhes sobre o volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Gerenciar seus volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
