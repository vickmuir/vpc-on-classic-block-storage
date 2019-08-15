---

copyright:
  years: 2019
lastupdated: "2019-07-03"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

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

# Visualizando volumes de armazenamento de bloco usando a CLI
{: #viewing-block-storage-cli}

Visualize detalhes sobre um volume do {{site.data.keyword.block_storage_is_short}} ou informações de resumo sobre todos os volumes por meio da CLI.
{:shortdesc}

## Antes
de Começar
{: #before-viewing-block-storage-cli}

1. Assegure-se de ter transferido por download, instalado e inicializado osvplug-ins da CLI a seguir:
    * CLI do {{site.data.keyword.cloud_notm}}
    * O plug-in de serviço de infraestrutura

   Para obter mais informações, consulte [Referência da CLI do {{site.data.keyword.cloud_notm}} para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Ao instalar o plug-in vpc-infrastructure pela primeira vez, deve-se configurar a geração de destino como gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Certifique-se de que já tenha [criado um {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Visualizar detalhes sobre um volume de armazenamento de bloco usando a CLI
{: #viewvol-cli}

Especifique este comando para mostrar detalhes sobre um volume.

```bash
ibmcloud is volume VOLUME_ID [--json]
```

Exemplo:

Este exemplo usa o ID do volume para mostrar detalhes do volume.

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Se seu volume estiver anexado a uma instância de servidor virtual, o nome e o ID do anexo do volume e da instância também serão exibidos.

## Visualizar todos os volumes de armazenamento de bloco usando a CLI
{: #viewall-vol-cli}

Execute este comando para listar informações resumidas sobre todos os volumes:

```bash
ibmcloud is volumes [--json]
```

Exemplo:

O exemplo a seguir mostra todos os volumes para todos os grupos de recursos em sua zona de disponibilidade.  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

Especificar o ID ou o nome do grupo de recursos filtra a lista para volumes que pertencem a um grupo de recursos. Quando você omite esse parâmetro, ele é padronizado como todos os grupos de recursos. Também é possível visualizar todos os volumes em uma determinada zona de disponibilidade.

Por padrão, os primeiros 25 volumes são exibidos por página.

## Visualizar detalhes sobre um anexo de volume usando a CLI
{: #viewvol-attachment-cli}

Execute este comando para visualizar detalhes de um anexo de volume para uma instância de servidor virtual:

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

Especifique um ID de instância e um ID de anexo de volume.  Como opção, exporte os detalhes no formato JSON.

## Visualizar detalhes sobre todos os anexos de volume usando a CLI

Execute este comando para visualizar todos os anexos de volume para uma instância de servidor virtual.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## Visualizar perfis de volume usando a CLI
{: #viewvol-profiles-cli}

Execute este comando para listar todos os perfis de volume disponíveis em sua região.

```bash
ibmcloud is volume-profiles [--json]
```

Exemplo:

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## Visualize um perfil de volume específico usando a CLI
{: #viewvol-profile-cli}

Execute este comando para visualizar um perfil de volume específico em sua região.

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME values are 10iops-tier, 5iops-tier, general-purpose, and custom.

Exemplo:

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

Você prefere usar o console do {{site.data.keyword.cloud}} para visualizar seus volumes de armazenamento de bloco? Para obter informações, consulte [Visualizando volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage).
{: tip}

## Próximas Etapas
{: #next-step-viewing-block-storage-cli}

Crie mais volumes ou gerencie seus volumes de armazenamento de bloco existentes.

* [Criando volumes de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [Gerenciando volumes de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
