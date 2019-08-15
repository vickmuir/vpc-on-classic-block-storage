---

Copyright:
  years: 2019
lastupdated: "2019-07-23"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, Key Protect, encryption, key management, Hyper Protect Crypto Services, HPCS, volume, data storage, virtual server instance, instance, customer-managed encryption

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Creación de volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente
{: #block-storage-encryption}

De forma predeterminada, los volúmenes de datos y de arranque de {{site.data.keyword.block_storage_is_short}} se cifran con cifrado gestionado por IBM. También puede crear volúmenes cifrados gestionados por el cliente utilizando un servicio de gestión de claves soportado para crear o importar la clave raíz del cliente. El cifrado gestionado por el cliente es una opción para los volúmenes de arranque y de datos que se crean durante el suministro de la instancia.  También puede especificar el cifrado gestionado por el cliente cuando cree un volumen de datos autónomo.
{:shortdesc}

## Servicios de gestión de claves para volúmenes de almacenamiento en bloque
{: #key-mgt-services-for-storage}

Hay dos servicios de gestión de claves disponibles: {{site.data.keyword.keymanagementserviceshort}} y {{site.data.keyword.hscrypto}} (disponibles en determinadas [regiones](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)). Los centros de datos de {{site.data.keyword.cloud_notm}} proporcionan un módulo de seguridad de hardware (HSM) dedicado para proteger las claves. La tabla siguiente contiene información acerca de cada servicio.

| Servicio de gestión de claves | Certificación de cifrado de HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conformidad con FIPS 140-2 *Nivel 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conformidad con FIPS 140-2 *Nivel 4* |
{: caption="Tabla 1. Servicios de gestión de claves para {{site.data.keyword.block_storage_is_short}}" caption-side="top"}

## Requisitos previos
{: #custom-managed-vol-prereqs}

Para crear volúmenes de almacenamiento en bloque con cifrado gestionado por el cliente, primero debe suministrar un servicio de gestión de claves y crear o importar la clave raíz del cliente.
También debe autorizar el acceso entre el servicio Cloud Block Storage y el servicio de gestión de claves. Cuando haya completado estos requisitos previos, puede empezar a crear volúmenes de almacenamiento en bloque que utilicen el cifrado gestionado por el cliente.

Los pasos siguientes son específicos de {{site.data.keyword.keymanagementserviceshort}}, pero el flujo general también se aplica a {{site.data.keyword.hscrypto}}.  Si utiliza {{site.data.keyword.hscrypto}}, consulte la [información sobre {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) para ver las correspondientes instrucciones.
{:note}

1. Suministre el servicio [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision).

   El suministro de una nueva instancia del servicio {{site.data.keyword.keymanagementserviceshort}} garantiza que se incluyen las actualizaciones más recientes, necesarias para el cifrado gestionado por el cliente de los volúmenes de almacenamiento en bloque. Las instancias de {{site.data.keyword.keymanagementserviceshort}} creadas en 2019 incluyen la extensión necesaria para dar soporte al cifrado gestionado por el cliente.
   {: tip}

2. [Cree](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) o [importe](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) una clave de raíz de cliente (CRK) en {{site.data.keyword.keymanagementservicelong_notm}}.
3. Desde IBM {{site.data.keyword.iamshort}} (IAM), [autorice el acceso](/docs/iam?topic=iam-serviceauth#serviceauth) entre **Cloud Block Storage** (servicio de origen) y **{{site.data.keyword.keymanagementserviceshort}}** (servicio de destino).

## Creación de volúmenes de datos cifrados gestionados por el cliente mediante la interfaz de usuario
{: #data-vol-encryption-ui}

Puede especificar el cifrado gestionado por el cliente cuando cree un nuevo volumen de almacenamiento en bloque durante el suministro de instancias o como un volumen autónomo.

Para crear un volumen cifrado cuando cree una instancia de servidor virtual, consulte [Creación de instancias de servidor virtual con cifrado gestionado por el cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok).

Para especificar el cifrado gestionado por el cliente cuando cree un volumen autónomo, siga estos pasos:

1. En la consola de {{site.data.keyword.cloud_notm}}, vaya a **icono de menú ![icono de menú](../../icons/icon_hamburger.svg) > Infraestructura VPC > Almacenamiento > Volúmenes de almacenamiento en bloque**.
Se mostrará una lista de todos los volúmenes de almacenamiento en bloque.
1. Seleccione **Nuevo volumen**.
1. En la página **Nuevo volumen de almacenamiento en bloque**, actualice los campos de la sección **Cifrado**. Consulte la tabla siguiente para obtener más información. Cuando termine de hacer cambios, pulse **Crear volumen**.

| Campo | Valor |
| ----- | ----- |
| Cifrado | _Gestionado por el proveedor_ es la modalidad de cifrado predeterminada. Para utilizar el cifrado gestionado por el cliente, seleccione un servicio de gestión de claves ({{site.data.keyword.keymanagementserviceshort}} o {{site.data.keyword.hscrypto}}). Si tiene varias instancias de servicio de gestión de claves suministradas en la cuenta, seleccione la que incluye la clave raíz del cliente que desea utilizar para el cifrado gestionado por el cliente. |
| Instancia servicio de cifrado | Si tiene varias instancias de servicio de gestión de claves suministradas en la cuenta, seleccione la que incluye la clave raíz del cliente que desea utilizar para el cifrado gestionado por el cliente. |
| Nombre de clave | Seleccione la clave de cifrado de datos en la instancia de {{site.data.keyword.keymanagementserviceshort}} que desea utilizar para cifrar el volumen. |
| ID de clave | Muestra el ID de clave que está asociado con la clave de cifrado de datos que ha seleccionado. |
{: caption="Tabla 1. Valores para el cifrado gestionado por el cliente" caption-side="top"}

## Creación de volúmenes de datos cifrados gestionados por el cliente mediante la CLI
{: #data-vol-encryption-cli}

Para crear un volumen de almacenamiento en bloque con cifrado gestionado por el cliente mediante la CLI, especifique el mandato `ibmcloud is volume-create` con el parámetro `--encryption-key`:

```bash
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--encryption-key ENCRYPTION_KEY] [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

El parámetro `--encryption-key` toma el CRN de la clave raíz. Obtenga el CRN de la clave raíz en la instancia de servicio de gestión de claves. Para obtener información, consulte la [documentación de la instancia de servidor virtual sobre cifrado gestionado por el cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli). Para obtener información sobre cómo crear volúmenes de almacenamiento en bloque mediante la CLI, consulte [Creación de volúmenes de almacenamiento en bloque mediante la CLI](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

En el ejemplo siguiente se muestra un nuevo volumen creado con cifrado gestionado por el cliente.

```bash
$ ibmcloud is volume-create demo_volume custom us-south-1 --iops 1000 --encryption-key abccorp-kp-vpc-2 5437644a-c4b1-447f-9646-b1a2a4df61382
Creating volume demovolume in resource group Default under account VPC 01 as user rtuser1@mycompany.com...
ID                                      933c8781-f7f5-4a8f-8a2d-3bfc711788ee
Name                                    demo_volume
Capacity                                100
IOPS                                    1000
Profile                                 custom
Encryption Key                          crn:v1:bluemix:public:kms:us-south:a/8d65fb1cf5e99e86dd7229ddef9e5b7b:b1abf7c5-381d-4f34-836e-5db7193250bc:key:fd57250e-908c-4785-a8a5-1f53176bcd2f
Encryption                              customer_managed
Status                                  pending
Resource Group                          Default(dbb12715c2a22f2bb60df4ffd4a543f2)
Created                                 2018-09-20 10:09:28
Zone                                    us-south-1
Volume Attachment Instance Reference    none
```
{:screen}

También puede crear volúmenes con cifrado gestionado por el cliente cuando suministre la instancia.  Para obtener información, consulte [Utilización de la CLI para suministrar instancias y volúmenes con cifrado gestionado por el cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli).

## Edición de volúmenes de arranque para que utilicen el cifrado gestionado por el cliente mediante la interfaz de usuario

Cuando cree una instancia desde la interfaz de usuario, puede especificar el cifrado gestionado por el cliente editando las propiedades del volumen de arranque. Para obtener información, consulte [Suministro de instancias de servidor virtual con volúmenes que utilizan cifrado gestionado por el cliente](docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-ui).
