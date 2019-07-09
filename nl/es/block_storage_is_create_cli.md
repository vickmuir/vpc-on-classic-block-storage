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

# Creación de volúmenes de almacenamiento en bloque mediante la CLI
{: #creating-block-storage-cli}

Puede crear volúmenes de {{site.data.keyword.block_storage_is_full}} mediante la interfaz de línea de mandatos (CLI).
{:shortdesc}

## Antes de empezar
{: #before-creating-block-storage-cli}

Asegúrese de que ha descargado, instalado e inicializado los siguientes plugins de la CLI:

* CLI de {{site.data.keyword.cloud_notm}}
* El plugin de servicio de la infraestructura

Para obtener más información, revise los requisitos previos en la [Consulta de CLI de IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Creación de un volumen de almacenamiento en bloque mediante la CLI
{: #create-vol-cli}

Ejecute el mandato siguiente.

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

Ejemplo:

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

La capacidad, que se indica en megabytes, puede oscilar entre los 10 y los 2000 GB.  Los valores de IOPS pueden estar comprendidos entre 1000 y 20000 IOPS, en función del tamaño del volumen. Si no especifica un valor de IOPS, se toma de forma predeterminada la configuración válida por perfil de volumen. Para obtener información, consulte la tabla de [Rangos de IOPS en función del tamaño de volumen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom).

El ID de volumen del ejemplo anterior se utiliza cuando se conecta almacenamiento en bloque a una instancia de servidor virtual, cuando se visualizan los detalles del volumen de almacenamiento en bloque y cuando se suprimen volúmenes.

¿Prefiere crear volúmenes de almacenamiento en bloque desde la consola de {{site.data.keyword.cloud}}? Para obtener información, consulte [Creación de volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).
{: tip}

## Pasos siguientes
{: #next-step-creating-block-storage-cli}

[Conecte un volumen de almacenamiento en bloque (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
