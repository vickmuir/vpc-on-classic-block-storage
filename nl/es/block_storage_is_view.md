---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance

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

# Visualización de detalles de un volumen de almacenamiento en bloque
{: #viewing-block-storage}

Vea detalles acerca de un volumen de almacenamiento en bloque o información de resumen sobre todos los volúmenes.

## Visualización de información sobre todos los volúmenes de almacenamiento en bloque
{: #viewvols}

Vaya a la lista de volúmenes de almacenamiento en bloque. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento > Volúmenes de almacenamiento en bloque para VPC**.

De forma predeterminada, se muestran los volúmenes de almacenamiento en bloque correspondientes a todos los grupos de recursos de la región.  En la lista de todos los **Volúmenes de almacenamiento en bloque**, verá la información siguiente.

| Campo | Descripción |
|-------|-------------|
| Estado | Estado del volumen, que funciona como el filtro predeterminado para todas las filas. Para obtener información acerca de los estados de volumen, consulte [Estados de volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#status). |
| Nombre | Pulse el nombre del volumen para ver los detalles del volumen individual. |
| Grupo de recursos |  Grupo de recursos definido al configurar la VPC. Los grupos de recursos gestionan el acceso a los recursos, pero no influyen sobre la facturación ni la supervisión.|
| Ubicación | Zona de disponibilidad en su región, heredada de la VPC (por ejemplo, US South 1). |
| Tamaño | Tamaño del volumen que ha especificado, en GB. |
| IOPS máx. | Número máximo de IOPS disponibles en el volumen, definido por el nivel IOPS de finalidad general o por el valor de IOPS personalizado que especifique. |
| Tipo de conexión | Datos para un volumen secundario conectado a una instancia, arranque cuando esté conectado como un volumen de arranque, o en blanco para un volumen que no esté conectado. |
| Cifrado | Gestionado por el proveedor o [gestionado por el cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption). |
| Acciones (...) | Pulse en los puntos suspensivos para visualizar un menú de acciones específicas de contexto que puede llevar a cabo.  Por ejemplo, un volumen disponible, no conectado tendría opciones de menú para conectarse a una instancia o para suprimir el volumen. |
{: caption="Tabla 1. Detalles sobre todos los volúmenes" caption-side="top"}

De forma predeterminada, se muestran 10 volúmenes en la lista de todos los volúmenes de almacenamiento en bloque.  Para cambiar este valor predeterminado, pulse la flecha hacia abajo y aumente la lista a 20 ó 50 volúmenes.  Utilice las flechas de la esquina inferior derecha para ir a la siguiente página y para volver a esta página.

## Visualización de detalles sobre un volumen de almacenamiento en bloque
{: #view-vol-details}

Para ver detalles acerca de un volumen de almacenamiento en bloque, vaya a la lista de todos los volúmenes de almacenamiento en bloque y seleccione un volumen.  En el caso de un solo volumen, verá la siguiente información.

| Campo | Descripción |
|-------|-------------|
| Nombre  | Nombre del volumen que ha especificado al crear el volumen. Pulse el icono de lápiz para editar el nombre del volumen. |
| Grupo de recursos | Grupo de recursos definido al configurar la VPC. Los grupos de recursos gestionan el acceso a los recursos, pero no influyen sobre la facturación ni la supervisión. |
| Tipo de conexión | Datos para un volumen secundario conectado a una instancia, arranque cuando esté conectado como un volumen de arranque, o en blanco para un volumen que no esté conectado. |
| ID | ID de volumen generado por el sistema. |
| Creado | Fecha generada por el sistema en que se creó el volumen. |
| Ubicación | Zona de disponibilidad en su región. |
| Tamaño | Tamaño del volumen que ha especificado. |
| Perfil | Nivel de IOPS o el perfil de IOPS personalizado. |
| IOPS máx. | Valor máximo de IOPS para un nivel de IOPS predefinido o el valor que ha especificado para IOPS personalizado. |
| Rendimiento | El rendimiento que puede ofrecer un disco, medido en Gigabits/segundo (Gbps).  En función de perfil de volumen, el rendimiento se calcula como la cantidad IOPS * tamaño de bloque de 16 K. |
| Cifrado | Gestionado por el proveedor o gestionado por el cliente. |
{: caption="Tabla 1.Detalles del volumen" caption-side="top"}

Los volúmenes conectados a una instancia de servidor virtual se visualizan en **Instancias conectadas** en la página **Detalles del volumen**.  También puede [Conectar un volumen a una instancia](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage).

Para un volumen conectado a una instancia, también puede ir a información sobre la instancia y luego volver a una lista de todos los volúmenes de almacenamiento en bloque.

## Visualización de detalles del volumen de almacenamiento en bloque conectado en detalles de la instancia

Puede ver información acerca de un volumen de almacenamiento en bloque conectado desde la página **Detalles de la instancia de servidor virtual**:

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external}, vaya a **icono de menú ![Icono de menú](../../icons/icon_hamburger.svg) > Cálculo > Instancias de servidor virtual para VPC** y seleccione una instancia.
1. En **Volúmenes de almacenamiento en bloque conectados**, pulse el nombre de un volumen para ir a la página de detalles del volumen.

¿Prefiere visualizar los volúmenes de almacenamiento en bloque mediante la CLI? Para obtener información, consulte [Visualización de volúmenes de almacenamiento en bloque (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage-cli).
{: tip}

## Pasos siguientes
{: #next-step-viewing-block-storage}

Cree más volúmenes o gestione los volúmenes de almacenamiento en bloque existentes.

* [Creación de volúmenes de almacenamiento en bloque en la consola de IBM Cloud](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)
* [Gestión de volúmenes de almacenamiento en bloque mediante la interfaz de usuario](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage)
