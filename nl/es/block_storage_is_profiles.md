---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, profile, volume profile, data storage, storage profile, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Perfiles de {{site.data.keyword.block_storage_is_short}}
{: #block-storage-profiles}

Cuando se suministran volúmenes secundarios de {{site.data.keyword.block_storage_is_short}} mediante la consola de {{site.data.keyword.cloud_notm}}, la CLI o la API, se especifica el perfil de IOPS que mejor se adapta a los requisitos de almacenamiento. Los perfiles están disponibles como tres niveles de IOPS predefinidos o como IOPS personalizados.  Los niveles de IOPS proporcionan un rendimiento de IOPS/GB garantizado para los volúmenes de hasta 2 TB de capacidad. También puede especificar un perfil de IOPS personalizado y definir la capacidad del volumen y la IOPS dentro de un rango.
{:shortdesc}

## Perfiles de IOPS por niveles
{: #tiers}

El almacenamiento en bloque proporciona tres niveles de IOPS predefinidos que puede seleccionar para especificar un rendimiento óptimo para las cargas de trabajo de cálculo y para evitar cuellos de botella. Puede suministrar volúmenes en la zona de disponibilidad con IOPS garantizadas, tal como se describe en la tabla siguiente:

| Nivel de IOPS | Carga de trabajo | Tamaño de volumen | IOPS máx. |
|-----------|----------|-------------|----------|
| 3 IOPS/GB | Cargas de trabajo de finalidad general: cargas de trabajo que alojan bases de datos pequeñas para aplicaciones web o que almacenan imágenes de disco de máquina virtual para un hipervisor | Entre 10 GB y 1 TB | Hasta 3.000 IOPS |
| | | Entre 1 TB y 2 TB | 3 IOPS/GB hasta 6.000 IOPS |
| 5 IOPS/GB | Cargas de trabajo de alta intensidad de E/S: cargas de trabajo caracterizadas por un alto porcentaje de datos activos, como por ejemplo bases de datos transaccionales y otras sensibles al rendimiento| Entre 10 GB y 600 GB | Hasta 3.000 IOPS |
| | | Entre 600 GB y 2 TB | 5 IOPS/GB hasta 10.000 IOPS|
| 10 IOPS/GB | Cargas de trabajo con gran consumo de almacenamiento: cargas de trabajo con gran cantidad de datos creadas por bases de datos NoSQL, procesos de datos para vídeo, aprendizaje automático y análisis | Entre 10 GB y 300 GB | Hasta 3.000 IOPS |
| | | Entre 300 GB y 2 TB | 10 IOPS/GB hasta 20.000 IOPS |
{: caption="Tabla 1. Perfiles de niveles de IOPS y niveles de rendimiento de cada uno" caption-side="top"}

El rendimiento máximo para todos los niveles de IOPS de almacenamiento en bloque es de 750 MB/s basado en un tamaño de bloque de 16 K

## Perfil de IOPS personalizado
{: #custom}

Las IOPS personalizadas constituyen una buena opción cuando se tienen requisitos de rendimiento bien definidos que no se encuentran dentro de un nivel de IOPS predefinido. Puede personalizar IOPS especificando el número total de IOPS para el volumen dentro del rango correspondiente a su tamaño de volumen. Puede suministrar volúmenes con entre 100 IOPS y 20.000 IOPS.

En la tabla siguiente se muestran los rangos de IOPS disponibles en función del tamaño del volumen.

| Tamaño de volumen (GB) | Rango de IOPS |
|-------------|--------------|
| 10 -39   | 100 - 1.000 |
| 40 - 79 | 100 -2.000 |
| 80 - 99 | 100 - 4.000 |
| 100 - 499 | 100 - 6.000 |
| 500 - 999 | 100 - 10.000 |
| 1.000 - 1.999 | 100 - 20.000 |
{: caption="Tabla 2. IOPS disponible en función del tamaño del volumen" caption-side="top"}

## Cómo se relacionan los perfiles de servidor virtual con los perfiles de almacenamiento
{: #vsi-profiles-relate-to-storage}

Los perfiles de servidor virtual son una combinación de vCPU y RAM de los que se pueden crear instancias rápidamente para iniciar una instancia de servidor virtual.  Puede seleccionar entre [tres familias de perfiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles) en función de los requisitos de su carga de trabajo.  Estos requisitos pueden ir desde cargas de trabajo comunes hasta cargas de trabajo con un alto consumo de CPU o de memoria.  

De forma similar, los perfiles de almacenamiento (niveles de IOPS o personalizados) proporcionan un rango de capacidad y rendimiento para los volúmenes secundarios.  De forma predeterminada, se crea un volumen de arranque primario de 100 GB cuando se crea una instancia de servidor virtual.  También puede crear y conectar volúmenes secundarios.  
Cuando se crea un volumen de datos secundario como parte de la creación de instancias, se selecciona el perfil de almacenamiento que mejor se adapta a los requisitos de almacenamiento para las cargas de trabajo de cálculo. En general, a medida que aumentan los requisitos de cálculo, se necesita un rendimiento de IOPS más alto.  En la tabla siguiente se muestra esta relación.

| Perfil de almacenamiento por nivel de IOPS | Perfil de servidor virtual |
|-----------------|------------------------|
| 3 IOPS/GB       | [Equilibrado](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#balanced) para cargas de trabajo comunes |
| 5 IOPS/GB       | [Cálculo](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#compute) para grandes demandas de CPU |
| 10 IOPS/GB      | [Memoria](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#memory) para cargas de trabajo con uso intensivo de memoria |
{: caption="Tabla 3. Relación entre los perfiles de almacenamiento en bloque y los perfiles de servidor virtual" caption-side="top"}

## Visualización de los perfiles de IOPS
{: #view-iops-profiles}

Puede ver los perfiles de IOPS disponibles en la consola de {{site.data.keyword.cloud_notm}}, en la CLI o en la API.

### Mediante la consola de IBM Cloud
{: using-console-iops-profile}

 Cuando [cree un volumen de almacenamiento en bloque desde la consola de {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage), seleccione **Niveles** en el menú desplegable.

 De forma alternativa, seleccione **Personalizado** y luego seleccione un valor de IOPS dentro del rango para ese tamaño de volumen. Pulse el enlace del tamaño de almacenamiento para ver una tabla de rangos de tamaño e IOPS.

 ### Mediante la CLI
 {: using-cli-iops-profiles}

 Para ver la lista de perfiles disponibles mediante la CLI, ejecute este mandato:
```
$ ibmcloud is volume-profiles
```
{:codeblock}

### Mediante la API
{: using-api-iops-profiles}

La siguiente solicitud de API de cURL recupera todos los perfiles de volumen.

```
curl -X GET \
$rias_endpoint/v1/volume/profiles?version=2019-05-31&generation=1 \
-H "Authorization: $iam_token"
```
{:codeblock}

## Información relacionada

Para ver información sobre los perfiles Equilibrado, Cálculo y Memoria de {{site.data.keyword.vsi_is_short}}, consulte el apartado sobre [Perfiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).
