---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, CLI, block storage volume, volume, volume attachment, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# Anexando um volume de armazenamento de bloco usando a CLI
{: #attaching-block-storage-cli}

Um anexo de volume conecta um volume de armazenamento de bloco a uma instância de servidor virtual. Cada instância pode ter [muitos anexos de volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits), mas um único anexo de volume conecta um volume a uma instância.

## Antes
de Começar
{: #before-attaching-block-storage-cli}

Certifique-se de que você tenha transferido por download, instalado e inicializado os plug-ins da CLI a seguir:

* CLI do {{site.data.keyword.cloud_notm}}
* CLI da API regional do {{site.data.keyword.cloud_notm}}

Para obter mais informações, consulte os pré-requisitos na [Referência da CLI do IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Anexar um volume de armazenamento de bloco usando a CLI
{: #attach-block-storage-cli}

Para anexar um volume a uma instância de servidor virtual no grupo de recursos atual, execute este comando.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` é o nome que você fornece para o anexo do volume e INSTANCE_ID é o ID do VSI.

O `VOLUME_ID `especifica o volume que você está anexando.

Especifique `-- auto-delete true` se você deseja que o volume seja excluído automaticamente quando o VSI for excluído.

Para ver uma lista de instâncias de servidor virtual disponíveis, execute o comando `ibmcloud is instances`.

Exemplo:

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.xxx.xx.xx    -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.xxx.xx.x     -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             192.xxx.xxx.xx   -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             192.xxx.xxx.xxx  -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## Mostrar detalhes de um volume anexado a uma instância de servidor virtual
{: #show-details-attached-vol}

Depois de anexar um volume, é possível exibir detalhes especificando o ID da instância e o ID do anexo do volume no comando `instance-volume-attachment`.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## Listar todos os anexos de volume de uma instância do servidor

Use o comando `instance-volume-attachments` e especifique o ID da instância para ver todos os anexos de volume para uma instância.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

Você prefere usar o console do {{site.data.keyword.cloud}}? Para obter informações sobre como os volumes são anexados no console, consulte [Anexando volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).
{:tip}

## Criar um JSON de anexo de volume
{: #volume_attachment_json}

Quando você provisiona uma instância de servidor virtual usando a CLI e cria um volume de armazenamento de bloco como parte do processo, deve-se especificar um JSON de anexo de volume. O JSON de conexão de volume, especificado no comando ou como um arquivo, define os parâmetros de volume. Quando você [cria uma instância](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) e especifica o parâmetro `--volume-attach`, você especifica o JSON do volume. Por exemplo, `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

Aqui está um arquivo JSON de anexo de volume de exemplo que define um volume customizado:

```
[
    {
        "name": "myvolume-attachment",
        "delete_volume_on_instance_delete": true,
        "volume": {
            "name": "myvolume",
            "capacity": 100,
            "iops": 1000,
            "profile": {
                "name": "custom"
            }
        }
    }
]
```
{: screen}

## Próximas Etapas
{: #next-step-attaching-block-storage-cli}

Crie volumes adicionais e gerencie os existentes. Consulte as informações a seguir.

* [Criar um volume de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [Gerenciando volumes de armazenamento de bloco usando a CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
