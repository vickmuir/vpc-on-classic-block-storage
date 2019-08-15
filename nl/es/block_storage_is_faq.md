---

copyright:
  years: 2019
lastupdated: "2019-07-03"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, boot volume, data volume, volume, data storage, virtual server instance, instance, IOPS

subcollection: vpc-on-classic-block-storage

---
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:screen: .screen}

# Preguntas frecuentes sobre {{site.data.keyword.block_storage_is_short}}
{: #block-storage-vpc-faq}

Bienvenido a la página de preguntas frecuentes sobre {{site.data.keyword.block_storage_is_short}}.  Este tema da respuestas a muchas de las preguntas sobre la creación y gestión de sus volúmenes de almacenamiento en bloque.  Si tiene otras preguntas que desea que se traten en este tema, envíe sus comentarios mediante los enlaces **Problemas** o **Editar tema**.
{:shortdesc}

## ¿Cómo puedo asignar almacenamiento para mis instancias?
{: faq}

Cuando cree una instancia de servidor virtual, puede [crear un volumen de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-from-vsi) que se conectará a dicha instancia.  También puede [crear volúmenes autónomos](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage#create-standalone-vol) y conectarlos luego a las instancias.

## ¿Cuántas instancias pueden compartir un volumen de almacenamiento en bloque suministrado?
{: faq}

Un volumen de almacenamiento en bloque solo se puede conectar a una instancia a la vez. Las instancias no pueden compartir el mismo volumen.

## ¿Cuántos volúmenes de almacenamiento en bloque secundarios (datos) se pueden conectar a una instancia?
{: faq}

Las instancias con menos de 4 vCPU pueden conectar un máximo de 4 volúmenes de almacenamiento en bloque.

Las instancias con 4 vCPU o más pueden conectar un máximo de 12 volúmenes secundarios de almacenamiento en bloque.

## Cuando se suministran IOPS, ¿las IOPS asignadas se imponen por instancia o por volumen?
{: faq}

Las IOPS se imponen a nivel de volumen.

## ¿Cómo se miden las IOPS?
{: faq}

Las IOPS se miden en base a un perfil de carga de bloques de 16 KB con un 50 % de escrituras y un 50 % de lecturas aleatorias. Las cargas de trabajo que difieren de este perfil pueden experimentar un rendimiento más bajo.

## ¿Qué son los perfiles de IOPS?
{: faq}

Los perfiles de IOPS definen el rendimiento de IOPS/GB para los volúmenes de varias capacidades. Hay tres [niveles de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) predefinidos que puede seleccionar que ofrecen un rendimiento de IOPS garantizado para cumplir los requisitos de la carga de trabajo. También puede definir [IOPS personalizadas](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) y especificar un rango de IOPS para el tamaño de volumen que elija. Las IOPS personalizadas constituyen una buena opción cuando se tienen requisitos de rendimiento bien definidos que no se encuentran dentro de un nivel de IOPS predefinido.

## ¿Cuál es el número máximo de IOPS que puedo esperar para mis volúmenes de datos?
{: faq}

El número máximo de IOPS para volúmenes de datos varía en función del tamaño del volumen y del perfil de nivel de IOPS que seleccione. Por ejemplo, el número máximo de IOPS para un volumen de finalidad general de hasta 1 TB es de 3.000 IOPS. Para obtener información, consulte [Perfiles de IOPS por niveles](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers). Si selecciona un [perfil de IOPS personalizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom), defina también un rango mínimo y máximo para un tamaño de volumen determinado.

## ¿Qué ocurre si utilizo un tamaño de bloque menor al medir el rendimiento?
{: faq}

Se puede obtener el número máximo de IOPS cuando se utilizan tamaños de bloque menores, aunque el rendimiento será menor. Por ejemplo, un volumen con 6000 IOPS tendrá el siguiente rendimiento en distintos tamaños de bloque:

* 16 KB * 6000 IOPS == ~93,75 MB/seg
* 8 KB * 6000 IOPS == ~46,88 MB/seg
* 4 KB * 6000 IOPS == ~23,44 MB/seg

## ¿Se me facturará por uso? ¿Existen límites de cuota?
{: faq}

Para obtener más información sobre cómo se le facturará, consulte los [Precios de Block Storage for VPC](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing). Se aplican ciertos límites.
Para obtener más información sobre las cuotas y los límites de su {{site.data.keyword.cloud}} Virtual Private Cloud y los recursos disponibles en el mismo, consulte [Cuotas](/docs/vpc-on-classic?topic=vpc-on-classic-quotas#quotas).

## Después de crear un volumen, ¿puedo aumentar su capacidad más tarde?
{: faq}

No, no puede aumentar la capacidad de un volumen. Le recomendamos que calcule la capacidad suficiente para el crecimiento estimado antes de suministrar un volumen de almacenamiento en bloque. Asimismo, considere cuántos volúmenes necesita y la capacidad de dichos volúmenes. Consulte [Gestión del recuento y capacidad de los volúmenes](/docs/vpc-on-classic?topic=vpc-on-classic-managingstoragelimits) para obtener más información.

## ¿El volumen debe precalentarse para alcanzar el rendimiento esperado?
{: faq}

No es necesario precalentar un volumen. Puede ver el rendimiento especificado inmediatamente después de suministrar el volumen.

## ¿Puedo crear volúmenes cifrados?
{: faq}

Todos los volúmenes de almacenamiento en bloque están cifrados, ya sea mediante el cifrado gestionado por IBM (valor predeterminado) o a través del servicio de protección de claves utilizando sus propias claves de cifrado. Para obtener información, consulte [Creación de volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).

## ¿Cómo puedo saber el tipo de cifrado que tiene un volumen?
{: faq}

En la interfaz de usuario, cuando visualice la lista de todos los volúmenes de almacenamiento en bloque, la columna Cifrado indica si se trata de cifrado gestionado por el proveedor o gestionado por el cliente.

Para ver las propiedades de un volumen desde la CLI, escriba:

```bash
ibmcloud is volume (VOLUME_NAME | VOLUME_ID)
```

## ¿Cuál es el nivel de seguridad de mis datos?
{: faq}

Todos los volúmenes de almacenamiento en bloque están cifrados en reposo mediante el cifrado gestionado por IBM o mediante sus propias claves de cifrado. Las claves gestionadas por IBM se generan y se almacenan de forma segura en una caja fuerte de almacenamiento en bloque respaldada por Consul y luego mantenida por el sistema. Las claves gestionadas por el cliente se gestionan de forma segura mediante el servicio IBM Key Protect.

## ¿Qué debo hacer en lo que respecta a copias de seguridad de datos para la recuperación tras desastre?
{: faq}

Block Storage for VPC protege sus datos en zonas de tolerancia a errores redundantes en la región. También le animamos a que haga copias de seguridad independientes de los datos. Tenga también en cuenta la posibilidad de utilizar [{{site.data.keyword.blockstoragefull}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started), que proporciona características de recuperación tras desastre, como por ejemplo clonación de volúmenes, instantáneas y duplicación.

## ¿Cuántos volúmenes puedo suministrar?
{: faq}

Puede suministrar un máximo de 1.000 volúmenes de almacenamiento en bloque por región.

## ¿Qué estrategia debo seguir para gestionar mis volúmenes?
{: faq}

Determine la capacidad que necesita en función del crecimiento estimado. El tamaño de volumen no se puede ampliar después del suministro. Sin embargo, puede crear nuevos volúmenes a medida que los necesite. Además, si tiene requisitos de rendimiento bien definidos, tenga en cuenta la posibilidad de elegir [IOPS personalizadas](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom), que proporcionan un rango específico de IOPS por tamaño de volumen.

## ¿Cómo se crea el disco de arranque para una instancia de servidor virtual y cómo se relaciona con el archivo de imagen?
{: faq}

El disco de arranque, también denominado volumen de arranque, se crea cuando se suministran una instancia de servidor virtual. El disco de arranque de una instancia es una imagen clonada de la imagen de la máquina virtual. El volumen de arranque se suprime cuando se suprime la instancia a la que está conectado.

## ¿Afectan al rendimiento los cortafuegos o los grupos de seguridad?
{: faq}

Como práctica recomendada, se recomienda ejecutar el tráfico de almacenamiento en una VLAN que omita el cortafuegos. La ejecución del tráfico de almacenamiento a través de cortafuegos de software aumenta la latencia y afecta negativamente al rendimiento del almacenamiento.

## ¿Cuándo se puede suprimir un volumen de datos de almacenamiento en bloque?
{: faq}

Solo puede suprimir un volumen de datos de almacenamiento en bloque cuando no esté conectado a una instancia de servidor virtual. [Desconecte el volumen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#detach) antes de suprimirlo. Los volúmenes de arranque se desconectan y se suprimen cuando se suprime la instancia.

## ¿Qué ocurre con mis datos cuando suprimo un volumen de datos de almacenamiento en bloque?
{: faq}

Cuando se suprime un volumen de datos de almacenamiento en bloque, todos los punteros a los datos de dicho volumen se eliminan y los datos pasan a estar completamente inaccesibles. Si luego vuelve a suministrar el almacenamiento físico en otra cuenta, se asigna un nuevo conjunto de punteros. Esta nueva cuenta no tiene manera de acceder a los datos que habían estado en el almacenamiento físico; el nuevo conjunto de punteros muestra todo ceros. Cuando se escriben datos nuevos en el volumen, los datos inaccesibles se sobrescriben.

## ¿Qué latencia de rendimiento puedo esperar de mi almacenamiento en bloque?
{: faq}

La latencia de destino dentro del almacenamiento es inferior a 1 milisegundo. El almacenamiento en bloque se conecta a instancias de cálculo de una red compartida, por lo que la latencia exacta de rendimiento dependerá del tráfico de la red dentro de un determinado periodo de tiempo.

## ¿Puedo configurar almacenamiento compartido en un clúster multizona?
{: faq}

En IBM Cloud, las opciones de almacenamiento están situadas en una zona de disponibilidad. No recomendamos gestionar almacenamiento compartido entre varias zonas.

Utilice en su lugar una opción de servicio clásica de datos de IBM Cloud, como {{site.data.keyword.cos_full}} o {{site.data.keyword.cloudantfull}}, si debe compartir los datos entre varias zonas y regiones.

## Tengo volúmenes en la infraestructura clásica. ¿Puedo trasladarlas a VPC?
{: faq}

No. La VPC proporciona acceso a nuevas zonas de disponibilidad en regiones multizona. Los recursos de cálculo, de red y de almacenamiento están diseñados específicamente para funcionar en la VPC.
