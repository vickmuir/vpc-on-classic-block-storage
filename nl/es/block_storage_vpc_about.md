---

copyright:
  years: 2019
lastupdated: "2019-06-14"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS, HPCS, Key Protect

subcollection: vpc-on-classic-block-storage

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Acerca de Block Storage for VPC
{: #block-storage-about}
[comment]: # (tema de ayuda enlazado)

{{site.data.keyword.block_storage_is_full}} (VPC) proporciona almacenamiento de datos de alto rendimiento montado en hipervisores para las instancias de servidor virtual (instancias) que puede suministrar dentro de una {{site.data.keyword.vpc_full}} (VPC). La infraestructura de VPC permite realizar un escalado rápido a través de varias regiones y zonas y ofrece rendimiento y seguridad adicionales. Para obtener más información acerca de {{site.data.keyword.vpc_short}}, consulte [Acerca de Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about).
{:shortdesc}

{{site.data.keyword.block_storage_is_short}} proporciona volúmenes de arranque primarios y volúmenes de datos secundarios. Los volúmenes de arranque se crean y se conectan automáticamente durante el suministro de la instancia. Los volúmenes de datos también se pueden crear y conectar durante el suministro de instancias, o como volúmenes autónomos que puede conectar posteriormente a una instancia. Para proteger los datos, puede utilizar su propia clave de cifrado o elegir el cifrado gestionado por IBM. Los [perfiles de niveles de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) le permiten especificar un nivel predefinido de rendimiento para sus volúmenes. También puede elegir un [perfil de IOPS personalizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) y definir su propia capacidad de volumen y el nivel de IOPS.

## Almacenamiento en bloque para volúmenes de VPC
{: #block-storage-vpc-volumes}

{{site.data.keyword.block_storage_is_short}} ofrece volúmenes de almacenamiento de datos a nivel de bloque que se pueden conectar a una instancia como volumen de arranque o como volumen de datos. Puede configurar un máximo de 750 volúmenes de almacenamiento en bloque por región. Puede conectar varios volúmenes de datos de almacenamiento en bloque a una sola instancia para obtener capacidad adicional. El número de volúmenes que puede conectar a una instancia depende de la cantidad de vCPU que contiene la instancia. Para obtener más información, consulte [Límites de conexión de volumen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits).

### Volúmenes de arranque
{: #block-storage-vpc-boot-volumes}

Cuando se crea una instancia, se crea automáticamente un volumen de arranque de 100 GB y se conecta a la instancia. El volumen de arranque tiene un máximo de 3.000 IOPS. Puede cifrar el volumen de arranque con [sus propias claves de cifrado](#about-customer-managed-encrytion) o bien puede utilizar el [cifrado gestionado por el proveedor](#about-provider-managed-encryption) predeterminado. Un volumen de arranque no se puede desconectar y suprimir manualmente, pero se suprime cuando se suprime la instancia.

### Volúmenes de datos secundarios
{: #secondary-data-volumes}

Los volúmenes de datos de almacenamiento en bloque son volúmenes secundarios con una capacidad total comprendida entre 10 GB y 2000 GB. El número máximo de IOPS para volúmenes de datos varía en función del tamaño del volumen y del perfil de nivel de IOPS que seleccione. Por ejemplo, el número máximo de IOPS para un volumen de finalidad general de hasta 1 TB es de 3.000 IOPS. Para obtener información, consulte [Perfiles de IOPS por niveles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers).

Los volúmenes de datos se crean como volúmenes autónomos o cuando se suministra una instancia. Los volúmenes autónomos permanecen en un estado no conectado hasta que el volumen se conecta a una instancia. Cuando se crea un volumen de datos como parte del suministro de una instancia, el volumen se conecta automáticamente a la instancia.  

Los volúmenes de datos de almacenamiento en bloque se pueden conectar a cualquier instancia disponible en su región, dentro de [determinados límites](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits). Estos volúmenes se desconectan de forma predeterminada cuando se suprime la instancia. La desconexión de forma predeterminada permite que los datos persistan más allá del ciclo de vida de la instancia de servidor virtual. Sólo se elimina la asociación del volumen con la instancia. Puede suprimir los volúmenes de datos manualmente después de que se desconecten o, al crear un volumen, puede especificar que se [se desconecten y se supriman automáticamente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#auto-delete) cuando se suprima la instancia.

Los volúmenes de datos se cifran de forma predeterminada con el cifrado gestionado por IBM. Si lo desea, puede cifrar los volúmenes de datos utilizando [su propia clave de cifrado](#about-customer-managed-encrytion).

## Cifrado de datos en reposo
{: #encryption}

{{site.data.keyword.cloud_notm}} se toma en serio la seguridad y comprende la importancia de poder cifrar los datos para mantenerlos protegidos. Cuando cree un volumen autónomo o cuando cree un volumen como parte de la creación de una instancia, puede elegir entre proteger los datos con el cifrado gestionado por el proveedor de IBM o utilizar claves de cifrado propias.  

### Cifrado gestionado por el proveedor
{: #about-provider-managed-encryption}

De forma predeterminada, todos los volúmenes de arranque y de datos se cifran con cifrado gestionado por el proveedor de IBM. Este servicio no tiene coste adicional ni afecta al rendimiento. El cifrado gestionado por el proveedor utiliza los siguientes protocolos estándares del sector:

* Cifrado AES-256
* Las claves se gestionan internamente con el protocolo KMIP (Key Management Interoperability Protocol)
* El almacenamiento cumple con los estándares Federal Information Processing Standard (FIPS) Publication 140-2, Federal Information Security Management Act (FISMA) y Health Insurance Portability and Accountability Act (HIPAA). También se ha validado el cumplimiento del almacenamiento con los estándares Payment Card Industry (PCI), Basel II, California Security Breach Information Act (SB 1386) y EU Data Protection Directive 95/46/EC.

### Cifrado gestionado por el cliente
{: #about-customer-managed-encrytion}

Puede cifrar los volúmenes de almacenamiento en bloque con sus propias claves de cifrado. En el caso de los volúmenes de datos, especifique el cifrado gestionado por el cliente al crear el volumen. En el caso de los volúmenes de arranque, puede editar las propiedades del volumen de arranque durante la creación de la instancia y especificar el cifrado gestionado por el cliente. Para ver los procedimientos, consulte [Creación de volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Si utiliza el cifrado gestionado por el cliente, la clave de cifrado se carga en un servicio de gestión de claves ({{site.data.keyword.keymanagementservicelong_notm}} o {{site.data.keyword.hscrypto}}). La infraestructura de VPC localiza la clave en la instancia del servicio de gestión de claves que ha configurado de antemano y luego cifra el volumen. Para ver los requisitos previos y un procedimiento de configuración de uso único, consulte [Creación de volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

Para obtener más información sobre la creación de cifrado gestionado por el cliente para volúmenes durante el suministro de una instancia de servidor virtual, consulte [Cifrado gestionado por el cliente para almacenamiento en bloque](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#customer-managed-encryption-keys).

## Información relacionada

Para obtener más información sobre la creación y la gestión de instancias en la VPC, consulte [Acerca de Virtual Servers for VPC](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-virtual-private-cloud#virtual-private-cloud).

Para empezar a crear almacenamiento en bloque para VPC, consulte [Creación de volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#creating-block-storage).

{{site.data.keyword.block_storage_is_short}} ofrece características exclusivas de la VPC y no es compatible con el almacenamiento de la infraestructura clásica. Si está interesado en {{site.data.keyword.blockstoragefull}} en la infraestructura clásica, consulte [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-About).
{:note}
