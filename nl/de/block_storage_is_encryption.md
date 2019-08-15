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

# Blockspeicherdatenträger mit benutzerverwalteter Verschlüsselung erstellen
{: #block-storage-encryption}

Standardmäßig werden {{site.data.keyword.block_storage_is_short}}-Bootdatenträger und -Datenträger für Daten mit von IBM verwalteter Verschlüsselung verschlüsselt. Sie können benutzerverwaltete verschlüsselte Datenträger jedoch auch erstellen, indem Sie über einen unterstützten Schlüsselmanagementservice einen Kundenrootschlüssel erstellen oder den Rootschlüssel importieren. Bei der benutzerverwalteten Verschlüsselung handelt es sich um eine Option für bei der Instanzbereitstellung erstellte Bootdatenträger und Datenträger für Daten.  Sie können die benutzerverwaltete Verschlüsselung auch angeben, wenn Sie einen eigenständigen Datenträger erstellen.
{:shortdesc}

## Schlüsselmanagementservices für Blockspeicherdatenträger
{: #key-mgt-services-for-storage}

Es stehen zwei Schlüsselmanagementservices zur Verfügung, {{site.data.keyword.keymanagementserviceshort}} und {{site.data.keyword.hscrypto}} (verfügbar in bestimmten [Regionen](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)). {{site.data.keyword.cloud_notm}}-Rechenzentren stellen ein dediziertes Hardwaresicherheitsmodul (HSM) bereit, um Ihre Schlüssel zu schützen. Die folgende Tabelle enthält Informationen zu den einzelnen Services.

| Schlüsselmanagementservice | HSM-Verschlüsselungszertifizierung |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2-Konformität (*Level 2*) |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2-Konformität (*Level 4*) |
{: caption="Tabelle 1. Schlüsselmanagementservices für {{site.data.keyword.block_storage_is_short}}" caption-side="top"}

## Voraussetzungen
{: #custom-managed-vol-prereqs}

Zum Erstellen von Blockspeicherdatenträgern mit benutzerverwalteter Verschlüsselung müssen Sie zunächst einen Schlüsselmanagementservice bereitstellen und Ihren Kundenrootschlüssel erstellen oder importieren.
Darüber hinaus müssen Sie auch für eine Autorisierung der Zugriffe von Cloud Block Storage auf den Schlüsselmanagementservice und umgekehrt sorgen. Wenn diese Voraussetzungen erfüllt sind, können Sie mit dem Erstellen von Blockspeicherdatenträgern beginnen, die eine benutzerverwaltete Verschlüsselung verwenden.

Die folgenden Schritte sind auf {{site.data.keyword.keymanagementserviceshort}} bezogen, der Ablauf gilt im Wesentlichen jedoch auch für {{site.data.keyword.hscrypto}}.  Wenn Sie {{site.data.keyword.hscrypto}} verwenden, finden Sie in den [Informationen zu {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) entsprechende Anleitungen.
{:note}

1. [Service '{{site.data.keyword.keymanagementserviceshort}}'](/docs/services/key-protect?topic=key-protect-provision#provision) bereitstellen

   Die Bereitstellung einer neuen {{site.data.keyword.keymanagementserviceshort}}-Serviceinstanz stellt sicher, dass die neuesten Aktualisierungen enthalten sind, die für eine benutzerverwaltete Verschlüsselung von Blockspeicherdatenträgern benötigt werden. 2019 erstellte {{site.data.keyword.keymanagementserviceshort}}-Instanzen enthalten die Erweiterung, die zur Unterstützung einer benutzerverwalteten Verschlüsselung erforderlich ist.
  {: tip}

2. [Erstellen](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) Sie einen Kundenrootschlüssel (Customer Root Key - CRK) oder
[importieren](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) Sie einen CRK in
{{site.data.keyword.keymanagementservicelong_notm}}.
3. Sorgen Sie über IBM {{site.data.keyword.iamshort}} (IAM) für eine [Autorisierung des Zugriffs](/docs/iam?topic=iam-serviceauth#serviceauth) zwischen **Cloud Block Storage** (Quellenservice) und **{{site.data.keyword.keymanagementserviceshort}}** (Zielservice).

## Datenträger mit benutzerverwalteter Verschlüsselung über die Benutzerschnittstelle erstellen
{: #data-vol-encryption-ui}

Sie können eine benutzerverwaltete Verschlüsselung beim Erstellen eines neuen Blockspeicherdatenträger während der Instanzbereitstellung oder als eigenständiger Datenträger angeben.

Informationen zum Erstellen eines verschlüsselten Datenträgers beim Erstellen einer virtuellen Serverinstanz finden Sie unter [Virtuelle Serverinstanzen mit benutzerverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-instance-creating-instances-byok).

Führen Sie die folgenden Schritte aus, um eine benutzerverwaltete Verschlüsselung beim Erstellen eines eigenständigen Datenträgers anzugeben:

1. Navigieren Sie in der {{site.data.keyword.cloud_notm}}-Konsole zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > VPC-Infrastruktur > Speicher > Blockspeicherdatenträger**.
Daraufhin wird eine Liste sämtlicher Blockspeicherdatenträger angezeigt.
1. Wählen Sie **Neuer Datenträger** aus.
1. Aktualisieren Sie auf der Seite **Neuer Blockspeicherdatenträger** die Felder im Bereich **Verschlüsselung**. Weitere Informationen hierzu finden Sie in der nachfolgenden Tabelle. Klicken Sie auf **Datenträger erstellen**, wenn alle Felder aktualisiert sind.

| Feld | Wert |
| ----- | ----- |
| Verschlüsselung | Der Modus _Vom Provider verwaltet_ ist der Standardverschlüsselungsmodus. Wählen Sie für eine benutzerverwaltete Verschlüsselung einen Schlüsselmanagementservice ({{site.data.keyword.keymanagementserviceshort}} oder {{site.data.keyword.hscrypto}}) aus. Die Schlüsselmanagementserviceinstanz sollte den Kundenrootschlüssel enthalten, der für die benutzerverwaltete Verschlüsselung verwendet werden soll. |
| Verschlüsselungsserviceinstanz | Wenn mehrere Schlüsselverwaltungsserviceinstanzen in Ihrem Konto bereitgestellt werden, wählen Sie die Instanz mit dem Kundenrootschlüssel aus, der für die benutzerverwaltete Verschlüsselung verwendet werden soll. |
| Schlüsselname | Wählen Sie den Datenverschlüsselungsschlüssel in der {{site.data.keyword.keymanagementserviceshort}}-Instanz aus, die zum Verschlüsseln des Datenträgers verwendet werden soll. |
| Schlüssel-ID | Zeigt die Schlüssel-ID an, die dem von Ihnen ausgewählten Datenverschlüsselungsschlüssel zugeordnet ist. |
{: caption="Tabelle 1. Werte für benutzerverwaltete Verschlüsselung" caption-side="top"}

## Benutzerverwaltete verschlüsselte Datenträger über die Befehlszeilenschnittstelle erstellen
{: #data-vol-encryption-cli}

Geben Sie zum Erstellen eines Blockspeicherdatenträgers mit benutzerverwalteter Verschlüsselung über die Befehlszeilenschnittstelle den Befehl `ibmcloud is volume-create` mit dem Parameter `--encryption-key` an:

```bash
ibmcloud is volume-create DATENTRÄGERNAME PROFILNAME ZONENNAME [--encryption-key VERSCHLÜSSELUNGSSCHLÜSSEL] [--capacity KAPAZITÄT] [--iops IOPS] [--resource-group-id RESSOURCENGRUPPEN-ID | --resource-group-name RESSOURCENGRUPPENNAME] [--json]
```

Für den Parameter `--encryption-key` wird der CRN des Rootschlüssels angegeben. Den CRN des Rootschlüssels können Sie in der Instanz des Schlüsselmanagementservice ermitteln. Informationen hierzu finden Sie in den Abschnitten zur benutzerverwalteten Verschlüsselung in der [Dokumentation zu virtuellen Serverinstanzen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli). Informationen zum Erstellen von Blockspeicherdatenträgern über die Befehlszeilenschnittstelle finden Sie unter [Blockspeicherdatenträger über die Befehlszeilenschnittstelle erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli).

Das folgende Beispiel verdeutlicht einen neuen, mit benutzerverwalteter Verschlüsselung erstellten Datenträger.

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

Sie können Datenträger mit benutzerverwalteter Verschlüsselung auch bei der Instanzbereitstellung erstellen.  Informationen hierzu finden Sie unter [Instanzen und Datenträger mit benutzerverwalteter Verschlüsselung über die Befehlszeilenschnittstelle bereitstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-cli).

## Bootdatenträger über die Benutzerschnittstelle für die Verwendung einer benutzerverwalteten Verschlüsselung bearbeiten

Wenn Sie eine Instanz über die Benutzerschnittstelle erstellen, können Sie eine benutzerverwaltete Verschlüsselung angeben, indem Sie die Eigenschaften des Bootdatenträgers bearbeiten. Informationen hierzu finden Sie unter [Virtuelle Serverinstanzen mit Datenträgern mit benutzerverwalteter Verschlüsselung bereitstellen](docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok#provision-byok-ui).
