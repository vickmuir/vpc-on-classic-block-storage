---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, VSI, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .Shortdesc}
{: codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .Aria-labeledby="caption"}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Creación de volúmenes de almacenamiento en bloque en la consola de {{site.data.keyword.cloud_notm}}
{: #creating-block-storage}
[comment]: # (tema de ayuda enlazado)

Puede crear un volumen de {{site.data.keyword.block_storage_is_short}} al crear una instancia de servidor virtual o puede crear un volumen autónomo para luego conectarlo a una instancia.
{:shortdesc}

Antes de empezar, asegúrese de que [ha creado un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Creación y conexión de un volumen de almacenamiento en bloque cuando se crea una instancia nueva
{: #create-from-vsi}

1. Cree una instancia. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Cálculo > Instancias de servidor virtual > Nueva instancia**.
1. [Configure la instancia de servidor virtual](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers). En **Volúmenes de almacenamiento en bloque conectados**, seleccione **Nuevo volumen de almacenamiento en bloque**.
1. Especifique la información que se describe en la tabla siguiente.  Cuando termine, pulse **Crear volumen**.

| Campo | Valor |
|-------|-------|
| Nombre  | Especifique un nombre significativo para el volumen, como por ejemplo un nombre que describa la función de cálculo o de carga de trabajo. Puede especificar una combinación de caracteres alfanuméricos y numéricos y luego editar el nombre si lo desea. |
| Perfil | Seleccione [Niveles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) y seleccione el nivel de rendimiento que necesita en la lista de IOP. Si los requisitos de rendimiento no se encuentran dentro de un nivel de IOPS predefinido, seleccione [Personalizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) y seleccione un valor de IOPS dentro del rango para ese tamaño de volumen. Pulse el enlace **tamaño de almacenamiento** para ver una tabla de rangos de tamaño e IOPS. |
| Supresión automática | Habilite esta característica para suprimir automáticamente este volumen cuando se suprima la instancia de servidor virtual conectada. Puede cambiar este valor más tarde en la página de detalles del servidor virtual. |
| IOPS | Seleccione 3, 5 o 10 IOPS/GB para un perfil por niveles |
| Tamaño | Especifique un tamaño de volumen en GB.  Los tamaños de volumen pueden estar comprendidos entre 10 GB y 2 TB. |
| Cifrado | El cifrado con claves gestionadas por IBM está habilitado de forma predeterminada en todos los volúmenes. También puede elegir **Gestionado por el cliente** y utilizar su propia clave de cifrado.  Para los requisitos previos y los pasos para configurar el cifrado gestionado por el cliente, consulte [Creación de volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
{: caption="Tabla 1. Valores de volumen de almacenamiento en bloque especificados al suministrar una instancia" caption-side="top"}

Se crea un volumen de almacenamiento en bloque y se conecta a la instancia de servidor virtual. En la página de detalles de la instancia, la lista **Volúmenes de almacenamiento en bloque conectados** se actualiza para mostrar el nuevo volumen.

Un volumen de almacenamiento en bloque solo se puede conectar a un servidor virtual a la vez. En la página de resumen del volumen de almacenamiento en bloque, puede ver detalles acerca de la instancia de servidor virtual seleccionando el nombre de la instancia en **Instancias conectadas**.

## Creación de un volumen de almacenamiento en bloque autónomo
{: #create-standalone-vol}

Puede crear un volumen de almacenamiento en bloque independiente del suministro de servidor virtual y conectar el volumen a una instancia más adelante.

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento > Volúmenes de almacenamiento en bloque** y seleccione **Nuevo volumen**.
1. Especifique la información de la tabla siguiente para definir el nuevo volumen de almacenamiento en bloque.
1. Cuando termine, pulse **Crear volumen**. Volverá a la página Volúmenes de almacenamiento en bloque, donde un mensaje indica que se está creando el volumen. Se muestra un segundo mensaje cuando se crea el volumen.
1. Para ver los detalles del nuevo volumen, seleccione el enlace **Ver recurso** en el segundo mensaje para ir a la página Detalles de volumen.

| Campo | Valor |
|-------|-------|
| Nombre  | Especifique un nombre significativo para el volumen. Por ejemplo, especifique un nombre que describa la función de cálculo o de carga de trabajo. Puede especificar un máximo de 40 caracteres alfanuméricos y luego puede editar el nombre. |
| Grupo de recursos | Especifique un grupo de recursos. Los grupos de recursos ayudan a organizar los recursos de la cuenta para facilitar su control de acceso y facturación. Para obtener información sobre cómo configurar un grupo de recursos, consulte [Métodos recomendados para organizar recursos en un grupo de recursos](/docs/resources?topic=resources-bp_resourcegroups#setuprgs). |
| Etiquetas | Especifique una etiqueta para organizar los recursos. El usuario asigna una etiqueta a un recurso para filtrar fácilmente los recursos en la lista de recursos. Para obtener información sobre las etiquetas, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag). |
| Ubicación | La zona de disponibilidad de su región, heredada de la VPC (por ejemplo, US South 1). |
| Tamaño | Especifique un tamaño de volumen en GB.  Los tamaños de volumen pueden estar comprendidos entre 10 GB y 2 TB. |
| IOPS | Seleccione [Niveles de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) y seleccione el mosaico con el nivel de rendimiento que necesita. |
| Personalizado | En función del tamaño del volumen que haya especificado, seleccione un valor de IOPS que esté dentro del rango para ese tamaño de volumen.  Pulse el enlace **tamaño de almacenamiento** para ver una tabla de rangos de tamaño e IOPS. Para obtener más información, consulte [Perfil de IOPS personalizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom). |
| Cifrado | El cifrado con claves gestionadas por IBM está habilitado de forma predeterminada en todos los volúmenes. Para utilizar sus propias claves de cifrado, elija una opción de cifrado gestionado por el cliente. Para obtener información, consulte [Creación de volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).|
{: caption="Tabla 2. Valores para definir un volumen de almacenamiento en bloque" caption-side="top"}

¿Prefiere crear volúmenes de almacenamiento en bloque mediante la CLI? Para obtener información, consulte [Creación de volúmenes de almacenamiento en bloque mediante la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).
{: tip}

## Pasos siguientes
{: #next-step-creating-block-storage}

Cuando renueva la página Volúmenes de almacenamiento en bloque, el nuevo volumen aparece en la parte superior de la lista de volúmenes. Si el volumen se ha creado correctamente, muestra el estado Disponible. En el caso de los volúmenes autónomos, la columna Tipo de archivo adjunto está en blanco (-). El menú Acción (...) que hay al final de una fila de la tabla contiene un enlace para [conectar un volumen de almacenamiento en bloque a una instancia](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Puede seguir creando más volúmenes de almacenamiento en bloque o gestionando los volúmenes existentes.

* [Visualización de detalles sobre un volumen de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Desconexión de un volumen de una instancia de servidor virtual](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach)
* [Supresión de un volumen de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#delete)
