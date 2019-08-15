---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, volume attachment, data storage, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Gestión de volúmenes de almacenamiento en bloque mediante la CLI
{: #managing-block-storage-cli}

Gestione {{site.data.keyword.block_storage_is_short}} desde la interfaz de línea de mandatos (CLI). Puede actualizar un nombre de volumen, actualizar una conexión de volumen, desconectar un volumen o suprimir un volumen.
{:shortdesc}

## Antes de empezar
{: #before-managing-block-storage-cli}

1. Asegúrese de que ha descargado, instalado e inicializado los siguientes plugins de la CLI:
    * CLI de {{site.data.keyword.cloud_notm}}
    * El plugin de servicio de la infraestructura

   Para obtener más información, consulte [Consulta de CLI de {{site.data.keyword.cloud_notm}} para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Al instalar el plugin vpc-infrastructure por primera vez, debe establecer la generación del destino en gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Asegúrese de que ya haya [creado una {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Actualización del nombre de un volumen
{: #update-vol-name}

Para cambiar el nombre de un volumen, especifique el nombre o el ID del volumen y luego indique el nuevo nombre.

```bash
ibmcloud is volume-update VOLUME_ID [--name NEW_NAME] [--json]
```

Ejemplo:

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

## Actualización de una conexión de volumen mediante la CLI
{: #update-vol-name-cli}

Puede actualizar el nombre de la conexión de un volumen y cambiar el valor predeterminado de supresión automática con el mandato `instance-volume-attachment-update`.

```bash
ibmcloud is instance-volume-attachment-update INSTANCE_ID VOLUME_ATTACHMENT_ID [--name NEW_NAME] [--auto-delete true | false] [--json]
```

Utilice el parámetro `--name` y especifique un nuevo nombre para la conexión del volumen.

Especifique `--auto-delete true` para suprimir automáticamente el volumen cuando suprima la instancia a la que está conectado.

Ejemplo que muestra los detalles de `Referencia de instancia de conexión de volumen`:

```
Vdisk Name    Vdisk ID                               Vdisk Type   Auto Delete   Instance Name   Instance ID
Vdisk-data1   fd146b1f-e1bb-4eab-ba78-3109e6bc3a2d   data         true          vsi-test1       8b56da93-7990-4ccf-9dc5-5aee6a5f08f9
```
{: screen}

## Desconexión de un volumen mediante la CLI
{: #detach-vol-attachment-cli}

Utilice el mandato `instance-volume-attachment-detach` para desconectar un volumen de una instancia y suprimir la conexión del volumen. El volumen de almacenamiento en bloque no se suprime; luego puede [conectarlo a otra instancia](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).

```bash
ibmcloud is instance-volume-attachment-detach INSTANCE_ID VOLUME_ATTACHMENT_ID [-f, --force]
```

## Supresión de un volumen de almacenamiento en bloque mediante la CLI
{: #delete-vol-cli}

Utilice el mandato `volume-delete` y especifique el ID del volumen para suprimir un volumen de almacenamiento en bloque.

**Nota:** no se puede suprimir un volumen de almacenamiento en bloque activo. Primero debe [desconectarlo del servidor virtual](#detach-vol-attachment-cli).

```bash
ibmcloud is volume-delete (VOLUME_NAME | VOLUME_ID) [-f, --force]
```

Ejemplo:

```bash
$ ibmcloud is volume-delete 64d85f0f-6c08-4188-9e9a-0057b3aa1b69
This will delete volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 and cannot be undone. Continue?> y
Deleting volume 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 under account MyAccount 01 as user user1@mycompany.com...
OK
Volume ID 64d85f0f-6c08-4188-9e9a-0057b3aa1b69 is deleted.
```
{: screen}

¿Prefiere gestionar los volúmenes de almacenamiento en bloque mediante la consola de {{site.data.keyword.cloud}}? Para obtener más información, consulte [Gestión de volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage).
{:tip}

## Pasos siguientes
{: #next-step-managing-block-storage-cli}

[Cree más volúmenes mediante la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

En el caso de que se produzcan problemas con volúmenes de almacenamiento en bloque existentes, es posible que pueda solucionar los problemas por su cuenta. Para obtener más información, consulte [Resolución de problemas de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
