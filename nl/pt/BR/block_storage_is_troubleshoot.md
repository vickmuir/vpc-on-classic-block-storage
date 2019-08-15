---

copyright:
  years: 2019
lastupdated: "2018-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot

subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Resolução de problemas do {{site.data.keyword.block_storage_is_short}}
{: #troubleshoot}

Ao criar ou gerenciar o {{site.data.keyword.block_storage_is_short}}, é possível encontrar problemas. Geralmente, é possível recuperar-se seguindo algumas etapas fáceis. Problemas, sintomas, prováveis causas e resoluções são descritos nas seções a seguir.
{:shortdesc}

## Não é possível recuperar um volume em uma região especificada
{: #troubleshoot-topic-1}

As informações sobre um ou mais volumes de armazenamento de bloco não puderam ser recuperadas para uma determinada região.
{: tsSymptoms}

Qualquer uma das causas a seguir pode se aplicar:

* O nome e as informações do volume estão ausentes na saída da UI ou da CLI.
* Talvez você também esteja tentando acessar um volume em uma região diferente da sua.
* Você pode estar tentando acessar um volume de geração 2.
{: tsCauses}

Verifique se o volume não foi removido de uma instância de servidor virtual e excluído. Procure a instância à qual você anexou o volume pela última vez na lista de todas as instâncias de servidor virtual:

1. No [Console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, navegue para **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Cálculo > Instâncias de servidor virtual**.

1. Selecione uma instância de servidor virtual na lista de todos os servidores virtuais.

Se o volume não estiver anexado conforme o esperado e não aparecer na lista de volumes, ele provavelmente foi excluído.  Como a exclusão de um volume remove completamente seus dados, ela não pode ser restaurada.  

Se você usar a CLI, verifique se inseriu a sintaxe correta para visualizar volumes. Consulte [Visualizar todos os volumes de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli). Verifique se você especificou o grupo de recursos ou a zona correta.
{: tsResolve}

## Não é possível excluir um volume por nome ou ID
{: #troubleshoot-topic-2}

Não é possível excluir um volume de armazenamento de bloco por nome ou ID.
{: tsSymptoms}

O nome do volume e o ID não são aceitos.
{: tsCauses}

Verifique se o nome ou o identificador do volume está correto e se o volume não está anexado a uma instância de servidor virtual. Além disso, verifique se o volume não está em um estado pendente.
{: tsResolve}
