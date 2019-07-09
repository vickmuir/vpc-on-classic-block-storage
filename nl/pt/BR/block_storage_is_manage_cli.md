---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# Gerenciando volumes de armazenamento de bloco usando a CLI
{: #managing-block-storage-cli}

Essas informações se aplicam ao {{site.data.keyword.cloud}} Virtual Private Cloud no ambiente de infraestrutura clássica.
{: important}

## Antes
de Começar
{: #before-managing-block-storage-cli}

Certifique-se de que você tenha transferido por download, instalado e inicializado os plug-ins da CLI a seguir:

* CLI do {{site.data.keyword.cloud_notm}}
* CLI da API regional do {{site.data.keyword.cloud_notm}}

Para obter mais informações, consulte os pré-requisitos na [Referência da CLI do IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Atualizar o nome de um volume
{: #update-vol-name}

Para mudar um nome de volume, especifique o nome ou o ID do volume e, em seguida, indique o novo nome.

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

Exemplo:

```bash
$ ibmcloud is volume-update 933c8781-f7f5-4a8f-8a2d-3bfc711788ee --name demo-volume-update
Updating volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount 01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo-volume-update
Capacity                                100
IOPS                                    1000
Profile                                 5iops-tier
Encryption                              -
Encryption                              provider managed
Status                                  available
Created                                 2019-05-20 10:09:28
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Zone                                    us-south-2
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Volume Attachment Instance Reference    none
```
{: screen}

## Atualizar um anexo de volume usando a CLI
{: #update-vol-name-cli}

É possível atualizar o nome do anexo de volume e mudar a configuração de exclusão automática padrão com o comando `instance-volume-attachment-update`.

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

Use o parâmetro `--name` e especifique um novo nome para o anexo de volume.

Especifique `-- auto-delete true` para excluir automaticamente o volume quando você excluir a instância à qual ele está anexado.

Exemplo mostrando detalhes para a `Referência da instância de anexo de volume`:

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## Remover um volume usando a CLI
{: #detach-vol-attachment-cli}

Use o comando `instance-volume-attachment-detach` para remover um volume de uma instância e excluir o anexo do volume. O volume de armazenamento de bloco não é excluído; é possível [anexá-lo a outra instância](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli) posteriormente.

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## Excluir um volume de armazenamento de bloco usando a CLI
{: #delete-vol-cli}

Use o comando `volume-delete` e especifique o ID do volume para excluir um volume de armazenamento de bloco.

**Nota:** não é possível excluir um volume de armazenamento de bloco ativo. Deve-se primeiro [removê-lo do servidor virtual](#detach-vol-attachment-cli).

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

Exemplo:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

Você prefere gerenciar volumes de armazenamento de bloco usando o console do {{site.data.keyword.cloud}}? Para obter mais informações, consulte [Gerenciando volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage).
{:tip}

## Próximas Etapas
{: #next-step-managing-block-storage-cli}

[Crie mais volumes usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

Para problemas com volumes de armazenamento de bloco existentes, você pode ser capaz de solucionar problemas e corrigi-los sozinho. Para obter mais informações, consulte
[Resolução de problemas de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
