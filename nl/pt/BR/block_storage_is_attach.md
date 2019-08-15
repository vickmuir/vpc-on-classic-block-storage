---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, block storage volume, volume, volume attachment, virtual server instance, instance

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

# Anexando um volume de armazenamento de bloco usando a UI
{: #attaching-block-storage}

Ao criar um volume do {{site.data.keyword.block_storage_is_short}} para uma instância de servidor virtual por meio da IU, o volume é anexo à instância por padrão. Quando você remove um volume, ele existe como um volume não anexado que pode ser reconectado posteriormente. Esses volumes disponíveis são exibidos na lista de [todos os volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). É possível anexar o volume a outra instância por meio da lista de todos os volumes de armazenamento de bloco ou ao visualizar detalhes sobre uma instância específica.
{:shortdesc}

## Limites de anexo de volume
{: #vol-attach-limits}

Embora seja possível anexar apenas um volume de armazenamento de bloco a uma instância de servidor virtual de cada vez, é possível anexar vários volumes de armazenamento de bloco diferentes a uma única instância, com os limites a seguir:

* Instâncias com menos de 4 CPUs virtuais podem anexar até 4 volumes secundários de armazenamento de bloco, além do volume de inicialização.
* Instâncias com 4 ou mais CPUs virtuais podem anexar até 12 volumes secundários de armazenamento de bloco, além do volume de inicialização.

## Anexar um volume de armazenamento de bloco a uma instância de servidor virtual
{: #attach}

Na lista de todos os volumes de armazenamento de bloco, siga estas etapas.

1. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, navegue até **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Armazenamento de bloco**.
1. Na lista de volumes, clique nas elipsis no final de uma linha para um volume disponível e não anexado.  Um menu de ação específica do contexto é exibido.
1. Selecione **Anexar à instância**.
1. Selecione um recurso de cálculo (instância do servidor virtual) na lista de recursos disponíveis e, em seguida, clique em **Anexar**.
1. As mensagens são exibidas na página de detalhes do volume indicando que o volume está sendo anexado à imagem.  Quando ele for concluído, o nome da imagem aparecerá em **Instâncias anexadas**.

Também é possível anexar um volume de armazenamento de bloco na página de detalhes da instância do servidor virtual.

1. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, navegue até **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Cálculo > Instâncias de servidor virtual**.
1. Selecione uma instância na lista de todas as instâncias do servidor virtual. Se houver quaisquer volumes de armazenamento de bloco anexados, você os verá listados em **Volumes de armazenamento de bloco anexados**.
1. Selecione **Anexar volume**.
1. Selecione um volume na lista de recursos disponíveis e clique em **Anexar**. As mensagens são exibidas na página de detalhes da instância indicando que o volume está sendo anexado.  Quando ele for concluído, a lista **Volumes de armazenamento de bloco anexados** será atualizada para incluir o novo volume.

Também é possível anexar manualmente volumes de armazenamento de bloco usando a CLI. Para obter informações, consulte [Anexando volumes de armazenamento de bloco (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
{: tip}

## Próximas Etapas
{: #next-step-attaching-block-storage}

Crie volumes adicionais e gerencie os existentes. Consulte as informações a seguir.

* [Criando volumes de armazenamento de bloco no console do IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gerenciando volumes de armazenamento de bloco usando a UI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
