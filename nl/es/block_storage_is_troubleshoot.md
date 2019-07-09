---

copyright:
  years: 2019
lastupdated: "2018-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot


subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Resolución de problemas de almacenamiento en bloque
{: #troubleshoot}

Cuando cree o gestione el almacenamiento en bloque, es posible que encuentre problemas. A menudo, puede solucionarlos siguiendo unos pocos pasos sencillos. En las secciones siguientes se describen los problemas, los síntomas, las causas probables y las resoluciones.
{:shortdesc}

## No se puede recuperar un volumen en una región especificada
{: #troubleshoot-topic-1}

No se ha podido recuperar información sobre uno o varios volúmenes de almacenamiento en bloque para una región determinada.
{: tsSymptoms}

Estas son las posibles causas:

* Falta el nombre y la información del volumen en la salida de la interfaz de usuario o de la CLI.
* Es posible que esté intentando acceder a un volumen de una región que no es su región.
* Es posible que esté intentando acceder a un volumen de generación 2.
{: tsCauses}

Compruebe que el volumen no se ha desconectado de una instancia de servidor virtual y se ha suprimido. Busque la instancia a la que ha conectado el volumen por última vez en la lista de todas las instancias de servidor virtual:

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Cálculo > Instancias de servidor virtual**.

1. Seleccione una instancia de servidor virtual en la lista de todos los servidores virtuales.

Si el volumen no está conectado como se esperaba y no aparece en la lista de volúmenes, es probable que se haya suprimido.  Debido a que la supresión de un volumen elimina por completo sus datos, no se puede restaurar.  

Si utiliza la CLI, verifique que ha especificado la sintaxis correcta para ver los volúmenes.  Consulte [Visualización de todos los volúmenes de almacenamiento en bloque desde la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli).  Verifique que ha especificado el grupo de recursos o la zona correctos.
{: tsResolve}

## No se puede suprimir un volumen por nombre o por ID
{: #troubleshoot-topic-2}

No se puede suprimir un volumen de almacenamiento en bloque por nombre o por ID.
{: tsSymptoms}

El nombre y el ID del volumen no se aceptan.
{: tsCauses}

Verifique que el nombre o el identificador del volumen son correctos y que el volumen no está conectado a una instancia de servidor virtual.  Verifique también que el volumen no está en estado pendiente.
{: tsResolve}
