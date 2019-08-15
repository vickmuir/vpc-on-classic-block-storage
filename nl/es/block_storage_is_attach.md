---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, block storage volume, volume, volume attachment, virtual server instance, instance

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

# Conexión de un volumen de almacenamiento en bloque mediante la IU
{: #attaching-block-storage}

Cuando se crea un volumen de {{site.data.keyword.block_storage_is_short}} para una instancia de servidor virtual desde la interfaz de usuario, el volumen se conecta a la instancia de forma predeterminada. Cuando desconecta un volumen, existe como un volumen desconectado que puede volver a conectar posteriormente. Estos volúmenes disponibles se muestran en la lista de [todos los volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). Puede conectar el volumen a otra instancia desde la lista de todos los volúmenes de almacenamiento en bloque o cuando visualice detalles acerca de una instancia determinada.
{:shortdesc}

## Límites de conexión de volúmenes
{: #vol-attach-limits}

Aunque solo puede conectar un volumen de almacenamiento en bloque a una instancia de servidor virtual a la vez, puede conectar varios volúmenes de almacenamiento en bloque distintos a una sola instancia, con los siguientes límites:

* Las instancias con menos de 4 CPU virtuales pueden conectar hasta 4 volúmenes secundarios de almacenamiento en bloque, más el volumen de arranque.
* Las instancias con 4 o más CPU virtuales pueden conectar hasta 12 volúmenes secundarios de almacenamiento en bloque, más el volumen de arranque.

## Conexión de un volumen de almacenamiento en bloque a una instancia de servidor virtual
{: #attach}

En la lista de todos los volúmenes de almacenamiento en bloque, siga estos pasos.

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento> Almacenamiento en bloque**.
1. En la lista de volúmenes, pulse los puntos suspensivos que hay al final de una fila para obtener un volumen desconectado disponible.  Se visualiza un menú de acciones específico del contexto.
1. Seleccione **Conectar a instancia**.
1. Seleccione un recurso de cálculo (instancia de servidor virtual) en la lista de recursos disponibles y luego pulse **Conectar**.
1. Se muestran mensajes en la página de detalles del volumen que indican que el volumen se está conectando a la imagen.  Cuando termina el proceso, el nombre de la imagen aparece bajo **Instancias conectadas**.

También puede adjuntar un volumen de almacenamiento en bloque desde la página de detalles de la instancia de servidor virtual.

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Cálculo > Instancias de servidor virtual**.
1. Seleccione una instancia en la lista de todas las instancias de servidor virtual. Si hay algún volumen de almacenamiento en bloque conectado, lo verá en la lista de **Volúmenes de almacenamiento en bloque conectados**.
1. Seleccione **Conectar volumen**.
1. Seleccione un volumen en la lista de recursos disponibles y pulse **Conectar**. Se muestran mensajes en la página de detalles de la instancia que indican que el volumen se está conectando.  Cuando finaliza el proceso, la lista **Volúmenes de almacenamiento en bloque conectados** se actualiza para incluir el nuevo volumen.

También puede conectar manualmente volúmenes de almacenamiento en bloque mediante la CLI. Para obtener información, consulte [Conexión volúmenes de almacenamiento en bloque (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).
{: tip}

## Pasos siguientes
{: #next-step-attaching-block-storage}

Cree volúmenes adicionales y gestione los existentes. Consulte la siguiente información.

* [Creación de volúmenes de almacenamiento en bloque en la consola de IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gestión de volúmenes de almacenamiento en bloque mediante la interfaz de usuario](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
