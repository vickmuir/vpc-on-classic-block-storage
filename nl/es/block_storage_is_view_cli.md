---

copyright:
  years: 2019
lastupdated: "2019-06-17"

Keywords: block storage, IBM CLoud, VPC, CLI, block storage volume, volume, IOPS

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

# Visualización de volúmenes de almacenamiento en bloque mediante la CLI
{: #viewing-block-storage-cli}

Vea detalles sobre un volumen de almacenamiento en bloque o información de resumen acerca de todos los volúmenes desde la CLI.

## Antes de empezar
{: #before-viewing-block-storage-cli}

Asegúrese de que ha descargado, instalado e inicializado los siguientes plugins de la CLI:

* CLI de {{site.data.keyword.cloud_notm}}
* CLI de API regional de {{site.data.keyword.cloud_notm}}

Para obtener más información, revise los requisitos previos en la [Consulta de CLI de {{site.data.keyword.cloud_notm}} para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Visualización de detalles sobre un volumen de almacenamiento en bloque mediante la CLI
{: #viewvol-cli}

Especifique este mandato para ver detalles sobre un volumen.

```bash
ibmcloud is volume VOLUME_ID [--json]
```

Ejemplo:

En este ejemplo se utiliza el ID de volumen para mostrar los detalles del volumen.

```bash
$ ibmcloud is volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Getting volume 933c8781-f7f5-4a8f-8a2d-3bfc711788ee under account MyAccount01 as user user1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          -
Encryption                              provider_managed
Profile                                 custom
Status                                  available
Resource Group                          Default(c16d1edde3fd4a71a0130aed371405a0)
Created                                 2019-05-15 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

Si el volumen está conectado a una instancia de servidor virtual, también se muestra el nombre y el ID de la conexión de volumen y la instancia.

## Visualización de todos los volúmenes de almacenamiento en bloque mediante la CLI
{: #viewall-vol-cli}

Ejecute este mandato para ver una lista de información de resumen sobre todos los volúmenes:

```bash
ibmcloud is volumes [--json]
```

Ejemplo:

En el ejemplo siguiente se muestran todos los volúmenes de todos los grupos de recursos de la zona de disponibilidad.  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

Si se especifica el ID o el nombre del grupo de recursos, la lista se filtra a los volúmenes que pertenecen a un grupo de recursos. Si omite este parámetro, de forma predeterminada se muestran todos los grupos de recursos. También puede ver todos los volúmenes de una zona de disponibilidad determinada.

De forma predeterminada, se muestran los primeros 25 volúmenes por página.

## Visualización de detalles sobre una conexión de volumen mediante la CLI
{: #viewvol-attachment-cli}

Ejecute este mandato para ver los detalles de una conexión de volumen con una instancia de servidor virtual:

```bash
ibmcloud is instance-volume-attachment INSTANCE_ID VOLUME_ATTACHMENT_ID [--json]
```

Especifique un ID de instancia y un ID de conexión de volumen.  Si lo desea, puede exportar los detalles en formato JSON.

## Visualización de detalles sobre todas las conexiones de volumen mediante la CLI

Ejecute este mandato para ver todas las conexiones de volumen correspondientes a una instancia de servidor virtual.

```bash
ibmcloud is instance-volume-attachments INSTANCE_ID [--json]
```

## Visualización de perfiles de volumen mediante la CLI
{: #viewvol-profiles-cli}

Ejecute este mandato para ver una lista de todos los perfiles de volúmenes disponibles en la región.

```bash
ibmcloud is volume-profiles [--json]
```

Ejemplo:

```bash
$ ibmcloud is volume-profiles
Listing volume profiles under account MyAccount 01 as user user1@mycompany.com...
Name             Family   Crn
generalpurpose1  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
generalpurpose2  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
custom           custom   crn:v1:public:globalcatalog::::volume.profile:custom
generalpurpose3  tiered   crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

## Visualización de un perfil de volumen específico mediante la CLI
{: #viewvol-profile-cli}

Ejecute este mandato para ver un perfil de volumen específico en la región.

```bash
ibmcloud is volume-profile PROFILE_NAME [--json]
```

PROFILE_NAME puede adoptar los siguientes valores: 10iops-tier, 5iops-tier, general-purpose y custom.

Ejemplo:

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

¿Prefiere utilizar la consola de {{site.data.keyword.cloud}} para ver los volúmenes de almacenamiento en bloque? Para obtener información, consulte [Visualización de volúmenes de almacenamiento en bloque](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage).
{: tip}

## Pasos siguientes
{: #next-step-viewing-block-storage-cli}

Cree más volúmenes o gestione los volúmenes de almacenamiento en bloque existentes.

* [Creación de volúmenes de almacenamiento en bloque (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [Gestión de volúmenes de almacenamiento en bloque (CLI)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
