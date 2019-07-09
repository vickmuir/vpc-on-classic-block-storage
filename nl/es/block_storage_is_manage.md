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

# Gestión de volúmenes de almacenamiento en bloque mediante la interfaz de usuario
{: #managing-block-storage}

## Desconexión de un volumen de almacenamiento en bloque de una instancia de servidor virtual
{: #detach}

Puede desconectar un volumen de almacenamiento en bloque que esté conectado actualmente a una instancia de servidor virtual.  Cuando se desconecta un volumen, se libera para que lo utilice otra instancia.

Para desconectar un volumen:

1. Vaya a la lista de todos los volúmenes de almacenamiento en bloque. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento> Volúmenes de almacenamiento en bloque para VPC**.
1. Localice el volumen y luego pulse los puntos suspensivos (...) que hay al final de la fila de la tabla. Aparecerá un
menú de contexto.
1. En el menú, pulse **Desconectar de instancia**.
1. Confirme pulsando **Desconectar instancia** en la ventana emergente.

De forma alternativa, puede pulsar un volumen individual de la lista de todos los volúmenes de almacenamiento en bloque e ir a la página **Detalles del volumen** de dicho volumen. En **Instancias conectadas**, pulse el signo menos que hay junto a la instancia de servidor virtual para desconectar el volumen de dicha instancia.

## Transferencia de un volumen de almacenamiento en bloque de una instancia de servidor virtual a otra
{: #transfer}

Para transferir un volumen de almacenamiento en bloque a otra instancia de servidor virtual:

1. [Desconecte el volumen de su instancia de servidor virtual](#detach).
1. Vaya a la instancia de servidor virtual a la que desea transferir el volumen. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Cálculo > Instancias de servidor virtual para VPC**.
1. Seleccione un servidor virtual de la lista.
1. En Volúmenes de almacenamiento conectados, pulse el signo más para añadir un volumen. Se muestran todos los volúmenes de almacenamiento en bloque.
1. En la lista de volúmenes, seleccione el volumen que ha desconectado anteriormente.

## Conexión de un volumen de almacenamiento en bloque conectado previamente
{: #reattach}

Los volúmenes de almacenamiento en bloque se conectan de forma predeterminada cuando se crea una nueva instancia de servidor virtual.  Cuando desconecta un volumen de una instancia, el volumen existe como volumen no conectado y se muestra en la lista de [todos los volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#viewvols). Puede conectarlo a otra imagen de la lista de volúmenes de almacenamiento en bloque.

1. Vaya a la lista de todos los volúmenes de almacenamiento en bloque. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento> Volúmenes de almacenamiento en bloque para VPC**.
1. Localice el volumen y luego pulse los puntos suspensivos (...) que hay al final de la fila de la tabla. Aparecerá un
menú de contexto.
1. En el menú, pulse **Conectar a instancia**.
1. Seleccione una instancia de servidor virtual disponible.
1. Confirme la selección.

## Cambio de nombre de un volumen de almacenamiento en bloque
{: #rename}

Puede cambiar el nombre de un volumen existente por uno más significativo.

1. Vaya a la lista de todos los volúmenes de almacenamiento en bloque. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento> Volúmenes de almacenamiento en bloque para VPC**.
1. Localice el volumen y luego pulse el nombre del volumen para ir a la página Detalles del volumen.
1. Pulse el icono de lápiz que hay tras el nombre del volumen y edite el nombre del volumen.
1. Confirme la edición.

## Supresión de un volumen de almacenamiento en bloque
{: #delete}

Cuando se suprime un volumen de almacenamiento en bloque, se eliminan sus datos por completo. El volumen no se puede restaurar.

No se puede suprimir un volumen de almacenamiento en bloque activo. Para suprimir un volumen, primero debe [desconectarlo](#detach) del servidor virtual y, a continuación, debe seguir estos pasos:

1. Vaya a la lista de todos los volúmenes de almacenamiento en bloque. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Almacenamiento> Volúmenes de almacenamiento en bloque para VPC**.
1. Localice el volumen que desea suprimir y pulse los puntos suspensivos que hay al final de la fila de la tabla. Aparecerá un
menú de contexto.
1. En el menú, pulse **Suprimir**.
1. Confirme la supresión.

## Supresión automática de volúmenes de datos de almacenamiento en bloque
{: #auto-delete}

Mediante la característica de supresión automática, puede especificar que se suprima automáticamente un volumen de datos de almacenamiento en bloque cuando se suprima una instancia a la que está conectado. Esta característica no se aplica a los volúmenes de arranque y está inhabilitada de forma predeterminada.

Para habilitar la supresión automática de un volumen de almacenamiento en bloque existente conectado a una instancia, siga estos pasos:

1. Localice la instancia de servidor virtual a la que está conectado el volumen. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}/vpc){: external} correspondiente a Virtual Private Cloud, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Cálculo > Instancias de servidor virtual para VPC**.
1. En **Volúmenes de almacenamiento en bloque conectados**, seleccione un volumen.
1. En el menú emergente, pulse el botón Supresión automática para habilitarlo.
1. Confirme la selección.

De forma alternativa, empiece seleccionando un volumen de la lista de volúmenes de almacenamiento en bloque (**Almacenamiento > Volúmenes de almacenamiento en bloque para VPC**).

Para habilitar la supresión automática en un nuevo volumen al crear una instancia, consulte [Creación y conexión de un volumen de almacenamiento en bloque al crear una nueva instancia](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi).

## Asignación de acceso a un volumen de almacenamiento en bloque
{: #assign-volume-access}

Con privilegios de administrador, puede asignar acceso de usuario a nivel de volumen al servicio {{site.data.keyword.block_storage_is_short}}. En la tabla siguiente se muestra la información que debe proporcionar en la [IU de Identity and Access Management (IAM)](/docs/iam?topic=iam-account_setup#assigning-access).

| Campo de IAM | Acción |
|--------|-------------|
| Servicios | Seleccione **Servicios de infraestructura** |
| Tipo de recurso | Seleccione **Block Storage for VPC** |
| ID de volumen | Especifique el [ID de volumen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage#view-vol-details) para asignar acceso a un volumen específico |
| Seleccione roles | Asigne roles de acceso a la plataforma, normalmente el de operador |

Para obtener más información, consulte las [prácticas recomendadas para asignar acceso](/docs/iam?topic=iam-account_setup#account_setup). Para ver el proceso completo de IAM, que incluye la invitación de usuarios a su cuenta y la asignación de acceso de IAM de Cloud, consulte la [guía de aprendizaje de iniciación de IAM](/docs/iam?topic=iam-getstarted#getstarted).

## Estado de un volumen de almacenamiento en bloque
{: #status}

En la tabla siguiente se muestran los estados que puede ver cuando se crean, se visualizan o se gestionan volúmenes de almacenamiento en bloque.

| Estado | Significado |
|--------|-------------|
| Disponible | Se ha recuperado correctamente un volumen |
| | Hay un volumen disponible y se puede conectar a una instancia |
| | Un volumen conectado está disponible para los datos
| | Hay un volumen de arranque disponibles |
| Error    | La creación del volumen ha fallado |
| | No se han podido recuperar todos los volúmenes de una región |
| | No se ha encontrado un volumen con el ID de volumen especificado |
| | No se ha podido suprimir un volumen |
| Pendiente | Se está creando un volumen |
| | Se está conectando un volumen a una instancia |
| Pendiente de supresión | Se está suprimiendo un volumen |

¿Prefiere gestionar los volúmenes de almacenamiento en bloque mediante la CLI? Para obtener información, consulte [Gestión de volúmenes de almacenamiento en bloque (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli).
{: tip}

## Pasos siguientes
{: #next-step-managing-block-storage}

Puede [crear volúmenes adicionales](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).

En el caso de que se produzcan problemas con volúmenes de almacenamiento en bloque existentes, es posible que pueda solucionar los problemas por su cuenta. Para obtener más información, consulte [Resolución de problemas de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-troubleshoot).
