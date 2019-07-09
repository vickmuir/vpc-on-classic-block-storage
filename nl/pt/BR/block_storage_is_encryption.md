---

Copyright:
  years: 2019
lastupdated: "2019-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Criando volumes de armazenamento de bloco com criptografia gerenciada pelo cliente
{: #block-storage-encryption}

Por padrão, os volumes de inicialização e de dados do {{site.data.keyword.block_storage_is_short}} são criptografados com a criptografia gerenciada pela IBM. Também é possível criar volumes criptografados gerenciados pelo cliente usando um serviço de gerenciamento de chave suportado para criar ou importar sua chave raiz do cliente. A criptografia gerenciada pelo cliente é uma opção para volumes de inicialização e dados criados durante o fornecimento da instância. Também é possível especificar a criptografia gerenciada pelo cliente quando você cria um volume de dados independente.  

## Serviços de gerenciamento de chave para volumes de armazenamento de bloco
{: #key-mgt-services-for-storage}

Dois serviços de gerenciamento de chave estão disponíveis, {{site.data.keyword.keymanagementserviceshort}} e {{site.data.keyword.hscrypto}} (disponíveis em determinadas [regiões](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)). Os data centers do {{site.data.keyword.cloud_notm}} fornecem um módulo de segurança de hardware (HSM) dedicado para proteger suas chaves. A tabela a seguir fornece informações sobre cada serviço.

| Serviço de gerenciamento de chave | Certificação de criptografia HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conformidade com FIPS 140-2 *Nível 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conformidade com FIPS 140-2 *Nível 4* |

## Pré-requisitos
{: #custom-managed-vol-prereqs}

Para criar volumes de armazenamento de bloco com criptografia gerenciada pelo cliente, deve-se primeiro provisionar um serviço de gerenciamento de chave e criar ou importar sua chave raiz do cliente.
Deve-se também autorizar o acesso entre o Cloud Block Storage e o serviço de gerenciamento de chave. Quando você tiver concluído esses pré-requisitos, será possível começar a criar volumes de armazenamento de bloco que usam a criptografia gerenciada pelo cliente.

As etapas a seguir são específicas do {{site.data.keyword.keymanagementserviceshort}}, mas o fluxo geral também se aplica ao {{site.data.keyword.hscrypto}}. Se você estiver usando {{site.data.keyword.hscrypto}}, consulte as [Informações do {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) para obter as instruções correspondentes.
{:note}

1. Forneça o serviço [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision).

   O fornecimento de uma nova instância de serviço do {{site.data.keyword.keymanagementserviceshort}} assegura que ela inclua as atualizações mais recentes necessárias para a criptografia gerenciada pelo cliente de volumes de armazenamento de bloco. As instâncias do {{site.data.keyword.keymanagementserviceshort}} criadas em 2019 incluem a extensão que é necessária para suportar a criptografia gerenciada pelo cliente.
   {: tip}

2. [Crie](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) ou
[importe](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) uma chave raiz do cliente (CRK) em
{{site.data.keyword.keymanagementservicelong_notm}}.
3. No IBM {{site.data.keyword.iamshort}} (IAM), [autorize o acesso](/docs/iam?topic=iam-serviceauth#serviceauth) entre o **Cloud Block Storage** (serviço de origem) e o **{{site.data.keyword.keymanagementserviceshort}}** (serviço de destino).

## Criando volumes de dados criptografados gerenciados pelo cliente usando a UI
{: #data-vol-encryption-ui}

É possível especificar a criptografia gerenciada pelo cliente ao criar um novo volume de armazenamento de bloco durante o fornecimento da instância ou como um volume independente.

Para criar um volume criptografado quando você cria uma instância de servidor virtual, consulte [Criando instâncias do servidor virtual com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok).

Para especificar a criptografia gerenciada pelo cliente ao criar um volume independente, siga estas etapas:

1. No console do {{site.data.keyword.cloud_notm}}, navegue para o **Ícone de menu ![Ícone de menu](../../icons/icon_hamburger.svg) > Infraestrutura VPC > Armazenamento > Volumes de armazenamento de bloco**.
É exibida uma lista de todos os volumes de armazenamento de bloco.
1. Selecione **Novo volume**. Na página Novo volume de armazenamento de bloco, atualize os campos na seção Criptografia.
1. Na página **Novo volume de armazenamento de bloco**, atualize os campos na seção **Criptografia**. Consulte a tabela a seguir para obter mais informações. Quando suas mudanças estiverem concluídas, clique em **Criar volume**.

| Campo | Value |
| ----- | ----- |
| Encryption | _Gerenciado pelo provedor_ é o modo de criptografia padrão. Para usar a criptografia gerenciada pelo cliente, selecione um serviço de gerenciamento de chave ({{site.data.keyword.keymanagementserviceshort}} ou {{site.data.keyword.hscrypto}}). A instância do serviço de gerenciamento de chave deve incluir a chave raiz do cliente que você deseja usar para a criptografia gerenciada pelo cliente. |
| Instância de serviço de criptografia | Se você tiver várias instâncias de serviço de gerenciamento de chave provisionadas em sua conta, selecione aquela que inclui a chave raiz do cliente que você deseja usar para criptografia gerenciada pelo cliente. |
| Nome principal | Selecione a chave de criptografia de dados dentro da instância do {{site.data.keyword.keymanagementserviceshort}} que você deseja usar para criptografar o volume. |
| ID da chave | Exibe o ID da chave que está associado à chave de criptografia de dados selecionada. |
{: caption="Tabela 1. Valores para criptografia gerenciada pelo cliente" caption-side="top"}

## Criando volumes de dados criptografados gerenciados pelo cliente usando a CLI
{: #data-vol-encryption-cli}

Para criar um volume de armazenamento de bloco com criptografia gerenciada pelo cliente usando a CLI, especifique o comando `ibmcloud is volume-create` com o parâmetro `--encryption-key`:

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

O parâmetro `--encryption-key` toma o CRN da chave raiz. Obtenha o CRN da chave raiz em sua instância de serviço de gerenciamento de chave. Para obter informações, consulte a [documentação da instância do servidor virtual sobre criptografia gerenciada pelo cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli). Para obter informações sobre a criação de volumes de armazenamento de bloco usando a CLI, consulte [Criando volumes de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

O exemplo a seguir mostra um novo volume criado com a criptografia gerenciada pelo cliente.

```bash
$ ibmcloud is volume-create demo_volume custom us-south-1 --iops 1000 --encryption-key abccorp-kp-vpc-2 5437644a-c4b1-447f-9646-b1a2a4df61382
Creating volume demovolume in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          crn:v1:bluemix:public:kms:us-south:a/8d65fb1cf5e99e86dd7229ddef9e5b7b:b1abf7c5-381d-4f34-836e-5db7193250bc:key:fd57250e-908c-4785-a8a5-1f53176bcd2f
Encryption                              customer_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Também é possível criar volumes com criptografia gerenciada pelo cliente durante o fornecimento da instância. Para obter informações, consulte [Usando a CLI para provisionar instâncias e volumes com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli).

## Editando volumes de inicialização para usar a criptografia gerenciada pelo cliente usando a UI

Ao criar uma instância por meio da UI, é possível especificar a criptografia gerenciada pelo cliente editando as propriedades do volume de inicialização. Para obter informações, consulte [Fornecendo instâncias do servidor virtual com volumes que usam a criptografia gerenciada pelo cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#provision-byok-ui).
