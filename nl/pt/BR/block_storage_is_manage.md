---

copyright:
  years: 2019
lastupdated: "2019-07-11"

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

# Gerenciando volumes de armazenamento de bloco usando a UI
{: #managing-block-storage}

Gerencie o {{site.data.keyword.block_storage_is_short}} por meio da IU. Separe um volume de uma instância de servidor virtual, transfira um volume de uma instância para outra, anexe um volume anexado anteriormente, renomeie um volume, configure a exclusão de volume automática, exclua manualmente um volume ou designe o acesso a um volume.
{:shortdesc}

## Remover um volume de armazenamento de bloco de uma instância de servidor virtual
{: #detach}

É possível remover um volume de armazenamento de bloco que está atualmente anexado a uma instância do servidor virtual.  A remoção libera o volume para uso por outra instância.

Para remover um volume:

1. Navegue para a lista de todos os volumes de armazenamento de bloco. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, acesse **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Armazenamento de bloco**.
1. Localize o volume e, em seguida, clique nas elipsis (...) no final da linha da tabela. Um menu de contexto é exibido.
1. No menu, clique em **Remover da instância**.
1. Confirme clicando em **Remover instância** no pop-up.

Como alternativa, é possível clicar em um volume individual na lista de todos os volumes de armazenamento de bloco e navegar para a página **Detalhes do volume** para esse volume. Em **Instâncias anexadas**, clique no sinal de menos ao lado da instância do servidor virtual para remover o volume dessa instância.

## Transferir um volume de armazenamento de bloco de uma instância de servidor virtual para outra
{: #transfer}

Para transferir um volume de armazenamento de bloco para outra instância de servidor virtual:

1. [Remova o volume de sua instância do servidor virtual](#detach).
1. Navegue para a instância do servidor virtual para a qual você deseja transferir o volume. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, acesse **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Cálculo > Instâncias de servidor virtual**.
1. Selecione um servidor virtual na lista.
1. Em volumes de Armazenamento anexado, clique no sinal de mais para incluir um volume. Todos os volumes de armazenamento de bloco são exibidos.
1. Na lista de volumes, selecione o volume que você removeu anteriormente.

## Anexar um volume de armazenamento de bloco anexado anteriormente
{: #reattach}

Os volumes de armazenamento de bloco são anexados por padrão quando você cria uma nova instância de servidor virtual.  Quando você remove um volume de uma instância, ele existe como um volume não anexado e é exibido na lista de [todos os volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). É possível anexá-lo a outra imagem na lista de volumes de armazenamento de bloco.

1. Navegue para a lista de todos os volumes de armazenamento de bloco. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, navegue até **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Armazenamento de bloco**.
1. Localize o volume e, em seguida, clique nas elipsis (...) no final da linha da tabela. Um menu de contexto é exibido.
1. No menu, clique em **Anexar à instância**.
1. Selecione uma instância de servidor virtual disponível.
1. Confirme sua seleção.

## Renomear um volume de armazenamento de bloco
{: #rename}

É possível mudar o nome de um volume existente para torná-lo mais significativo.

1. Navegue para a lista de todos os volumes de armazenamento de bloco. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, acesse **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Armazenamento de bloco**.
1. Localize o volume e, em seguida, clique no nome do volume para ir para a página Detalhes do volume.
1. Clique no ícone de lápis após o nome do volume e edite o nome.
1. Confirme sua edição.

## Excluir um volume de armazenamento de bloco
{: #delete}

A exclusão de um volume de armazenamento de bloco remove completamente seus dados. O volume não pode ser restaurado.

Não é possível excluir um volume de armazenamento de bloco ativo. Para excluir um volume, primeiro [remova-o](#detach) do servidor virtual e, em seguida, siga estas etapas:

1. Navegue para a lista de todos os volumes de armazenamento de bloco. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, acesse **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Armazenamento > Armazenamento de bloco**.
1. Localize o volume que você deseja excluir e, em seguida, clique nas elipsis no final da linha da tabela. Um menu de contexto é exibido.
1. No menu, clique em **Excluir**.
1. Confirme a exclusão.

## Exclusão automática de volumes de dados de armazenamento de bloco
{: #auto-delete}

Usando o recurso Exclusão automática, é possível especificar que um volume de dados de armazenamento de bloco seja excluído automaticamente quando você excluir uma instância à qual ele está anexado. Esse recurso não se aplica aos volumes de inicialização e é desativado por padrão.

Para ativar a Exclusão automática de um volume de armazenamento de bloco existente anexado a uma instância, siga estas etapas:

1. Localize a instância do servidor virtual à qual o volume está anexado. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} para a Nuvem particular virtual, navegue até **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Cálculo > Instâncias de servidor virtual**.
1. Em **Volumes de armazenamento de bloco anexados**, selecione um volume.
1. No menu pop-up, clique no botão de Exclusão automática para ativar.
1. Confirme sua seleção.

Como alternativa, comece selecionando um volume na lista de volumes de armazenamento de bloco (**Armazenamento > Armazenamento de bloco**).

Para ativar a Exclusão automática em um novo volume ao criar uma instância, consulte [Criar e anexar um volume de armazenamento de bloco ao criar uma nova instância](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi).

## Designar acesso a um volume de armazenamento de bloco
{: #assign-volume-access}

Com privilégios de Administrador, é possível designar acesso de usuário de nível de volume para o serviço do {{site.data.keyword.block_storage_is_short}}. A tabela a seguir mostra as informações que devem ser fornecidas na [UI do Identity and Access Management (IAM)](/docs/iam?topic=iam-account_setup#assigning-access).

| Campo do IAM | Ação |
|--------|-------------|
| Serviços | Selecione **Serviços de infraestrutura** |
| Tipo de recurso | Selecione **Armazenamento de bloco para VPC** |
| ID do volume | Insira o [ID do volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) para designar acesso a um volume específico |
| Selecione Funções | Designe funções de acesso da plataforma, geralmente, Operador |
{: caption="Tabela 1. Informações para o IAM" caption-side="top"}

Para obter mais informações, consulte as [melhores práticas para designar acesso](/docs/iam?topic=iam-account_setup#account_setup). Para o processo completo do IAM, que inclui convidar usuários para sua conta e designar acesso ao Cloud IAM, consulte o [Tutorial de introdução do IAM](/docs/iam?topic=iam-getstarted#getstarted).

## Status do volume de armazenamento de bloco
{: #status}

A tabela a seguir mostra os status que você pode ver ao criar, visualizar ou gerenciar seus volumes de armazenamento de bloco.

| Status | Significado |
|--------|-------------|
| Disponíveis | Um volume foi recuperado com êxito |
| | Um volume está disponível e pode ser anexado a uma instância |
| | Um volume anexado está disponível para dados
| | Um volume de inicialização está disponível |
| Com falha    | Falha na criação de volume |
| | Todos os volumes em uma região não puderam ser recuperados |
| | Um volume com o ID de volume especificado não pôde ser localizado |
| | Um volume não pôde ser excluído |
| Pendente | Um volume está sendo criado |
| | Um volume está sendo anexado a uma instância |
| Exclusão pendente | Um volume está sendo excluído |
{: caption="Tabela 2. Status de armazenamento de bloco" caption-side="top"}

Você prefere gerenciar volumes de armazenamento de bloco usando a CLI? Para obter informações, consulte [Gerenciando volumes de armazenamento de bloco (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli).
{: tip}

## Próximas Etapas
{: #next-step-managing-block-storage}

É possível [criar volumes adicionais](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

Para problemas com volumes de armazenamento de bloco existentes, você pode ser capaz de solucionar problemas e corrigi-los sozinho. Para obter mais informações, consulte [Resolução de problemas de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
