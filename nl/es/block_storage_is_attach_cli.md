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


# Conexión de un volumen de almacenamiento en bloque mediante la CLI
{: #attaching-block-storage-cli}

Una conexión de volumen conecta un volumen de almacenamiento en bloque a una instancia de servidor virtual. Cada instancia puede tener [muchas conexiones de volúmenes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits), pero solo una conexión de volumen se conecta a una instancia.

## Antes de empezar
{: #before-attaching-block-storage-cli}

Asegúrese de que ha descargado, instalado e inicializado los siguientes plugins de la CLI:

* CLI de {{site.data.keyword.cloud_notm}}
* CLI de API regional de {{site.data.keyword.cloud_notm}}

Para obtener más información, revise los requisitos previos en la [Consulta de CLI de IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Conexión de un volumen de almacenamiento en bloque mediante la CLI
{: #attach-block-storage-cli}

Para conectar un volumen a una instancia de servidor virtual en el grupo de recursos actual, ejecute este mandato.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANCE_ID VOLUME_ID [--auto-delete true | false] [--json]
```

`NAME` es el nombre que proporciona para la conexión de volumen e INSTANCE_ID es el ID de la VSI.

El valor de `VOLUME_ID` especifica el volumen que está conectando.

Especifique `--auto-delete true` si desea que el volumen se suprima automáticamente cuando se suprima la VSI.

Para ver una lista de las instancias de servidor virtual disponibles, ejecute el mandato `ibmcloud is instances`.

Ejemplo:

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

## Visualización de los detalles de un volumen conectado a una instancia de servidor virtual
{: #show-details-attached-vol}

Después de conectar un volumen, puede visualizar detalles especificando el ID de instancia y el ID de conexión del volumen en el mandato `instance-volume-attachment`.

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

## Listado de todas las conexiones de volumen de una instancia de servidor

Utilice el mandato `instance-volume-attachments` y especifique el ID de instancia para ver todas las conexiones de volumen correspondientes a una instancia.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

¿Prefiere utilizar la consola de {{site.data.keyword.cloud}}? Para obtener información sobre cómo se conectan los volúmenes en la consola, consulte [Conexión de volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).
{:tip}

## Creación de un archivo JSON de conexión de volumen
{: #volume_attachment_json}

Cuando suministre una instancia de servidor virtual mediante la CLI y cree un volumen de almacenamiento en bloque como parte del proceso, debe especificar un archivo JSON de conexión de volumen. El archivo JSON de conexión de volumen, que se especifica en el mandato o como un archivo, define los parámetros del volumen. Cuando se [crea una instancia](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) y se especifica el parámetro `--volume-attach`, se especifica el archivo JSON del volumen. Por ejemplo, `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

A continuación se muestra un archivo JSON de conexión de volumen de ejemplo que define un volumen personalizado:

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

## Pasos siguientes
{: #next-step-attaching-block-storage-cli}

Cree volúmenes adicionales y gestione los existentes.  Consulte la siguiente información.

* [Creación de un volumen de almacenamiento en bloque mediante la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [Gestión de volúmenes de almacenamiento en bloque mediante la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
