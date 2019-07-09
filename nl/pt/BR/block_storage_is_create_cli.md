---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Criando volumes de armazenamento de bloco usando a CLI
{: #creating-block-storage-cli}

É possível criar volumes do {{site.data.keyword.block_storage_is_full}} usando a interface da linha de comandos (CLI).
{:shortdesc}

## Antes
de Começar
{: #before-creating-block-storage-cli}

Assegure-se de ter transferido por download, instalado e inicializado osvplug-ins da CLI a seguir:

* CLI do {{site.data.keyword.cloud_notm}}
* O plug-in de serviço de infraestrutura

Para obter mais informações, consulte os pré-requisitos na [Referência da CLI do IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Criar um volume de armazenamento de bloco usando a CLI
{: #create-vol-cli}

Execute o comando a seguir.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Exemplo:

```bash
$ ibmcloud is volume-create demovolume1 custom us-south-1 --iops 1000
Creating volume demovolume1 in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demovolume1
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

A capacidade, indicada em megabytes, pode variar de 10 a 2.000 GBs. Os valores IOPS podem ser de 1.000 a 20.000 IOPS, dependendo do tamanho do volume. Se você não especificar um valor IOPS, ele será padronizado para a configuração válida por perfil de volume. Para obter informações, consulte a tabela de [Intervalos de IOPS com base no tamanho do volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).

O ID do volume no exemplo acima é usado ao anexar o armazenamento de bloco a uma instância de servidor virtual, visualizando detalhes do volume de armazenamento de bloco e excluindo volumes.

Você prefere criar volumes de armazenamento de bloco por meio do console do {{site.data.keyword.cloud}}? Para obter informações, consulte [Criando volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
{: tip}

## Próximas Etapas
{: #next-step-creating-block-storage-cli}

[Anexar um volume de armazenamento de bloco (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
