---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Criando volumes de armazenamento de bloco no console do {{site.data.keyword.cloud_notm}}
{: #creating-block-storage}
[comment]: # (tópico da ajuda vinculado)

É possível criar um volume de armazenamento de bloco ao criar uma instância do servidor virtual ou criar um volume independente para anexar posteriormente a uma instância.
{:shortdesc}

Antes de iniciar, certifique-se de ter [criado um {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Criar e anexar um volume de armazenamento de bloco ao criar uma nova instância
{: #create-from-vsi}

1. Crie uma instância. No
[Console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular
virtual, navegue para **Ícone de menu
![Ícone de menu](../../icons/icon_hamburger.svg) > Cálculo > Instâncias do servidor virtual para VPC > Nova instância**.
1. [Configure
sua instância de servidor virtual](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers). Em Volumes de armazenamento de bloco
anexados**, selecione **Novo volume de armazenamento de
bloco**.
1. Insira as informações descritas na tabela a seguir. Quando concluído, clique em
**Criar volume**.

| Campo | Value |
|-------|-------|
| Nome  | Especifique um nome significativo para o seu volume, por exemplo, um nome que descreva sua função de cálculo ou de carga de trabalho. É possível inserir uma combinação de caracteres alfabéticos e numéricos e, posteriormente, editar o nome se desejar. |
| Perfil | Selecione [Camadas](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) e selecione o nível de desempenho necessário na lista de IOPs. Se seus requisitos de desempenho não se enquadram em uma camada de IOPS predefinida, selecione [Customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) e selecione um valor IOPS dentro do intervalo para esse tamanho de volume. Clique no link **tamanho do armazenamento** para ver uma tabela de intervalos de tamanho e IOPS. |
| Exclusão Automática | Ative esse recurso para excluir automaticamente esse volume quando a instância do servidor virtual anexada for excluída. É possível mudar essa configuração posteriormente na página de detalhes do servidor virtual. |
| IOPS | Selecione 3, 5 ou 10 IOPS/GB para um perfil em Camada |
| Tamanho | Insira um tamanho de volume em GBs. Os tamanhos de volume podem estar entre 10 GB e 2 TBs. |
| Encryption | A criptografia com chaves gerenciadas pela IBM é ativada por padrão em todos os volumes. Também é possível escolher **Gerenciado pelo cliente** e usar sua própria chave de criptografia. Para pré-requisitos e etapas para configurar a criptografia gerenciada pelo cliente, consulte [Criando volumes de armazenamento de bloco com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Tabela 1. Valores de volume de armazenamento de bloco especificados ao provisionar uma instância" caption-side="top"}

Um volume de armazenamento de bloco é criado e anexado à instância do servidor virtual. Na página de detalhes da instância, a lista **Volumes de armazenamento de bloco anexados** é atualizada para mostrar o novo volume.

Um volume de armazenamento de bloco pode ser anexado apenas a um servidor virtual de cada vez. Na página de resumo do volume de armazenamento de bloco, é possível visualizar detalhes sobre a instância do servidor virtual selecionando o nome da instância em **Instâncias anexadas**.

## Criar um volume de armazenamento de bloco independente
{: #create-standalone-vol}

É possível criar um volume de armazenamento de bloco independente do fornecimento do servidor virtual e anexar o volume a uma instância posteriormente.

1. No [Console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, navegue para **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Volumes de armazenamento de bloco para VPC** e selecione **Novo volume**.
1. Insira as informações na tabela abaixo para definir seu novo volume de armazenamento de bloco.
1. Quando concluído, clique em **Criar volume**. Você é retornado para a página Volumes de armazenamento de bloco, em que uma mensagem indica que o volume está sendo criado. Uma segunda mensagem é exibida quando o volume é criado.
1. Para ver detalhes do novo volume, selecione o link **Visualizar recurso** na segunda mensagem para navegar para a página Detalhes do volume.

| Campo | Value |
|-------|-------|
| Nome  | Especifique um nome significativo para o volume. Por exemplo, forneça um nome que descreva sua função de cálculo ou de carga de trabalho. É possível inserir até 40 caracteres alfanuméricos e editar o nome posteriormente. |
| Grupo de recursos | Especifique um grupo de recursos. Os grupos de recursos ajudam a organizar os recursos da conta para propósitos de controle de acesso e faturamento. Para obter informações sobre a configuração de um grupo de recursos, consulte [Melhores práticas para organizar recursos em um grupo de recursos](/docs/resources?topic=resources-bp_resourcegroups#setuprgs). |
| Tags | Especifique uma tag para organizar seus recursos. Uma tag é um rótulo que você designa a um recurso para filtragem fácil de recursos em sua lista de recursos. Para obter informações sobre tags, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag). |
| Localização | A zona de disponibilidade em sua região, herdada do VPC (por exemplo, Sul dos EUA 1). |
| Tamanho | Insira um tamanho de volume em GBs.  Os tamanhos do volume podem estar entre 10 GB a 2 TBs. |
| IOPS | Selecione [Camadas IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) e selecione o tile com o nível de desempenho necessário. |
| Customizado | Dependendo do tamanho do volume especificado, selecione um valor IOPS dentro do intervalo para esse tamanho de volume. Clique no link **tamanho do armazenamento** para ver uma tabela de intervalos de tamanho e IOPS. Para obter mais informações, consulte [Perfil IOPS customizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). |
| Encryption | A criptografia com chaves gerenciadas pela IBM é ativada por padrão em todos os volumes. Para usar suas próprias chaves de criptografia, escolha uma opção de criptografia gerenciada pelo cliente. Para obter informações, consulte [Criando volumes de armazenamento de bloco com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).|
{: caption="Tabela 2. Valores para definir um volume de armazenamento de bloco" caption-side="top"}

Você prefere criar volumes de armazenamento de bloco usando a CLI? Para obter informações, consulte [Criando volumes de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).
{: tip}

## Próximas Etapas
{: #next-step-creating-block-storage}

Quando você atualiza a página Volumes de armazenamento de bloco, o novo volume aparece na parte superior da lista de volumes. Se o volume foi criado com êxito, ele mostra um status de Disponível. Para volumes independentes, a coluna Tipo de anexo está em branco (-). O menu Ação (...) no final de uma linha da tabela fornece um link para [anexando um volume de armazenamento de bloco a uma instância](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

É possível continuar criando mais volumes de armazenamento de bloco ou gerenciar volumes existentes.

* [Visualizar detalhes sobre um volume de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Remover um volume de uma instância de servidor virtual](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [Excluir um volume de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
