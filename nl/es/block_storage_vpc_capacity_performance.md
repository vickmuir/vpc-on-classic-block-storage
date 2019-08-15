---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, volume capacity, classic, virtual server

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
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Rendimiento y capacidad de {{site.data.keyword.block_storage_is_short}}
{: #capacity-performance}

Es importante elegir tamaño y el nivel de rendimiento óptimos del volumen de almacenamiento en bloque para sus cargas de trabajo. Cuando se suministra {{site.data.keyword.block_storage_is_short}} desde la interfaz de usuario o desde la CLI, se puede elegir la capacidad del volumen y el nivel de rendimiento.
{:shortdesc}

## Capacidad
{: #block-storage-vpc-capacity}

Puede especificar entre 10 GB y 2000 GB (2 TB) de capacidad por volumen de datos de almacenamiento en bloque en incrementos de 1 GB. La capacidad total del volumen se determina cuando se selecciona un [perfil de IOPS](#iops-profiles). Los volúmenes de arranque son de 100 GB.

## Perfiles de IOPS
{: #iops-profiles}

Cuando se suministran volúmenes de {{site.data.keyword.block_storage_is_short}}, se especifica el [perfil de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) que mejor se adapte a los requisitos de almacenamiento. Los perfiles están disponibles como tres niveles de IOPS predefinidos o como IOPS personalizados. Los [niveles de IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) proporcionan un rendimiento de IOPS/GB garantizado para los volúmenes de hasta 2 TB de capacidad. También puede especificar un perfil de [IOPS personalizado](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) y definir la capacidad del volumen y la IOPS dentro de un rango. Utilice la consola de {{site.data.keyword.cloud_notm}}, la CLI o la API para especificar un perfil.

## Cómo afecta el tamaño de bloque al rendimiento
{: #how-block-size-affects-performance}

La IOPS se basa en un tamaño de bloque de 16 KB con una carga de trabajo aleatoria de 50 % lectura/escritura al 50/50. Un bloque de 16 KB es el equivalente de una escritura en el volumen. El rendimiento base se determina por la cantidad de IOPS multiplicada por el tamaño de bloque de 16 KB. Cuanto más alto sea la IOPS que especifique, más alto es el rendimiento. El rendimiento máximo de un volumen de almacenamiento en bloque es de 750 MB/s.

El tamaño de bloque que elija para la aplicación afecta directamente al rendimiento del almacenamiento. Si el tamaño de bloque es inferior a 16 KB, el límite de IOPS se alcanza antes que el límite de rendimiento. Por el contrario, si el tamaño de bloque es superior a 16 KB, el límite de rendimiento se alcanza antes que el límite de IOPS. En la tabla siguiente se muestran algunos ejemplos de cómo afectan al rendimiento el tamaño de bloque y la IOPS, calculado como Tamaño medio de E/S x IOPS = Rendimiento en MB/s.

| Tamaño de bloque (KB) | IOPS | Rendimiento (MB/s) |
|-----------------|------|-------------------|
| 4 (típico para Linux) | 1.000 | 4 |
| 8 (típico para Oracle) | 1.000  | 8 |
| 16 | 1.000 | 16 |
| 32 (típico para SQL Server) | 500 | 16 |
| 64 | 250 | 16 |
| 128 | 128 | 16 |
{: caption="Tabla 1. Ejemplos de cómo afectan al rendimiento el tamaño de bloque y la IOPS" caption-side="top"}
