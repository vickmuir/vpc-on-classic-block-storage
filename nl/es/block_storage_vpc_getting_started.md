---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, getting started, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:shortdesc: .shortdesc}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Iniciación a {{site.data.keyword.block_storage_is_short}}
{: #getting-started}

Esta guía de aprendizaje le ayuda a empezar a crear volúmenes de {{site.data.keyword.block_storage_is_short}} en una nube privada virtual.
{: .shortdesc}

## Antes de empezar
{: #block-storage-before-you-begin}

Para empezar, revise primero el contenido que le puede ayudar con la implementación. ¿Es un nuevo usuario de {{site.data.keyword.cloud}} y {{site.data.keyword.block_storage_is_short}}? La información siguiente le puede resultar de ayuda:

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [Acerca de Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

Regístrese para una cuenta de {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Registro para {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}.

## Paso 1: Determinar los requisitos de almacenamiento
{: #determine-storage-requirements}

¿Ejecutando cargas de trabajo de finalidad general con requisitos de almacenamiento modestos? ¿O bien sus cargas de trabajo hacer un gran uso de la capacidad de E/S y requieren una mayor capacidad y rendimiento? Para obtener más información sobre cómo se determina la capacidad y el rendimiento, consulte [Capacidad y rendimiento de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance). Consulte también el apartado [Perfiles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) para obtener información sobre la opción de perfil de IOPS que mejor se adapta a sus requisitos de almacenamiento. 

¿También va a crear una instancia de servidor virtual? Consulte [cómo se relacionan los perfiles de servidor virtual con los perfiles de almacenamiento](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage).

## Paso 2: Calcular el tamaño y el precio del almacenamiento en bloque
{: #size-price-block-storage}

Seleccione un [perfil por niveles de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) para el volumen de almacenamiento en bloque.  Opcionalmente, si tiene requisitos de rendimiento bien definidos que no se encuentran dentro de un nivel de IOPS predefinido, elija un [perfil de IOPS personalizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). 

Después de elegir el tamaño y el rendimiento de los volúmenes de almacenamiento en bloque, consulte la información sobre [Precios](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing) para calcular el precio de los volúmenes ver cómo se le facturará.

## Paso 3: Iniciar una sesión en la cuenta de {{site.data.keyword.cloud_notm}}
{: block-storage-log-into-ibm-account}

Acceda al formulario de pedido de {{site.data.keyword.block_storage_is_short}} desde el [catálogo de {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: external}. Utilice su IBMid y su contraseña.

## Paso 4 (opcional): Verificar el acceso a {{site.data.keyword.vpc_short}}

Si desea crear un volumen dentro de una nube privada virtual, primero debe [crear una VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console). Omita este paso si desea crear un volumen autónomo fuera de la VPC. Luego puede solicitar acceso a {{site.data.keyword.vpc_short}} para acceder a una instancia y conectar un volumen de almacenamiento en bloque que ha creado de forma independiente. Para obtener más información acerca de {{site.data.keyword.vpc_short}}, consulte la [Guía de aprendizaje de iniciación de VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Paso 5: Crear volúmenes de almacenamiento en bloque

Empiece a crear volúmenes en la [consola de {{site.data.keyword.cloud_notm}} (UI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage) o mediante la [CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli) o la [API de {{site.data.keyword.vpc_short}}](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}. Para obtener más información sobre cómo utilizar las herramientas de IBM Cloud Developer para instalar la CLI de IBM Cloud, consulte [Iniciación a las herramientas de IBM Cloud Developer](/docs/cli?topic=cloud-cli-getting-started).

## Pasos siguientes
{: #next-step-block-storage-getting-started}

Después de crear almacenamiento en bloque, explore más opciones:

* [Vea detalles sobre el volumen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Gestione los volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
