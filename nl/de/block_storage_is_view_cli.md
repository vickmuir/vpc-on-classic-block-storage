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

# Blockspeicherdatenträger über die Befehlszeilenschnittstelle anzeigen
{: #viewing-block-storage-cli}

Zeigen Sie Details zu einem Blockspeicherdatenträger oder Übersichtsdaten zu allen Datenträgern über die Befehlszeilenschnittstelle an.

## Vorbereitungen
{: #before-viewing-block-storage-cli}

Stellen Sie sicher, dass Sie die folgenden Plug-ins für die Befehlszeilenschnittstelle heruntergeladen, installiert und initialisiert haben:

* {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle
* {{site.data.keyword.cloud_notm}} Regional API-Befehlszeilenschnittstelle

Weitere Informationen finden Sie im Abschnitt zu den Voraussetzungen in der [Referenz zur {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle für VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).

## Details zu einem Blockspeicherdatenträger über die Befehlszeilenschnittstelle anzeigen
{: #viewvol-cli}

Geben Sie zum Anzeigen von Details zu einem Datenträger den folgenden Befehl an:

```bash
ibmcloud is volume DATENTRÄGER-ID [--json]
```

Beispiel:

Bei dem folgenden Beispiel wird die Datenträger-ID zum Anzeigen von Datenträgerdetails verwendet.

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

Ist Ihr Datenträger einer virtuellen Serverinstanz zugeordnet, werden auch Name und ID der Datenträgerzuordnung angezeigt.

## Alle Blockspeicherdatenträger über die Befehlszeilenschnittstelle anzeigen
{: #viewall-vol-cli}

Führen Sie den folgenden Befehl aus, um Übersichtsdaten für alle Datenträger aufzulisten:

```bash
ibmcloud is volumes [--json]
```

Beispiel:

Das folgende Beispiel enthält eine Auflistung aller Datenträger für die Ressourcengruppen in Ihrer Verfügbarkeitszone.  

```bash
$ ibmcloud is volumes
Listing volumes under account MyAccount 01 as user user1@mycompany.com...
ID                                     Name              Capacity   IOPS   Auto Delete   Encryption        Profile         Created               Status      Zone         Resource Group
a3f4d60a-c9cf-4666-9a2a-0b1d85f92c19   demo_volume1      50         10     Manual        provider managed  generalpurpose   2019-06-30 11:04:46  pending     us-south-1   (c16d1edd-.)
3aaa0beb-83ac-4b2f-b4f5-eab382d1a5aa   demo_volume2      50         100    Manual        provider managed  custom           2019-06-30 10:26:34  available   us-south-1   (c16d1edd-.)
6d9713cf-9688-486d-b8c9-d9f1c6e7876c   demo_volume3      50         100    Manual        provider managed  custom           2019-06-30 10:39:24  available   us-south-1   (c16d1edd-.)
```
{: screen}

Durch Angabe der ID oder des Namens einer Ressourcengruppe wird die Liste der Datenträger gefiltert und es werden nur Datenträger angezeigt, die zu der jeweiligen Ressourcengruppe gehören. Wenn Sie diesen Parameter nicht angeben, werden standardmäßig alle Ressourcengruppen verwendet. Sie können auch alle Datenträger in einer bestimmten Verfügbarkeitszone anzeigen.

Standardmäßig werden die ersten 25 Datenträger pro Seite angezeigt.

## Details zu einer Datenträgerzuordnung über die Befehlszeilenschnittstelle anzeigen
{: #viewvol-attachment-cli}

Führen Sie den folgenden Befehl aus, um Details zu einer Datenträgerzuordnung einer virtuellen Serverinstanz anzuzeigen:

```bash
ibmcloud is instance-volume-attachment INSTANZ-ID DATENTRÄGERZUORDNUNGS-ID [--json]
```

Geben Sie eine Instanz-ID und eine ID für die Datenträgerzuordnung an. Bei Bedarf können Sie die Details auch im JSON-Format exportieren.

## Details zu allen Datenträgerzuordnungen über die Befehlszeilenschnittstelle anzeigen

Führen Sie den folgenden Befehl aus, um alle Datenträgerzuordnungen einer virtuellen Serverinstanz anzuzeigen.

```bash
ibmcloud is instance-volume-attachments INSTANZ-ID [--json]
```

## Datenträgerprofile über die Befehlszeilenschnittstelle anzeigen
{: #viewvol-profiles-cli}

Führen Sie den folgenden Befehl aus, um alle Datenträgerprofile aufzulisten, die in Ihrer Region verfügbar sind.

```bash
ibmcloud is volume-profiles [--json]
```

Beispiel:

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

## Ein bestimmtes Datenträgerprofil über die Befehlszeilenschnittstelle anzeigen
{: #viewvol-profile-cli}

Führen Sie den folgenden Befehl aus, um ein bestimmtes Datenträgerprofil in Ihrer Region anzuzeigen.

```bash
ibmcloud is volume-profile PROFILNAME [--json]
```

Zulässige Werte für PROFILNAME sind: 10iops-tier, 5iops-tier, general-purpose und custom.

Beispiel:

```bash
$ ibmcloud is volume-profile generalpurpose1
Getting volume profile generalpurpose1 under account MyAccount 01 as user user1@mycompany.com...
Name     generalpurpose1
Family   tiered
Crn      crn:v1:public:globalcatalog::::volume.profile:generalpurpose
```
{: screen}

Zeigen Sie die Blockspeicherdatenträger lieber in der {{site.data.keyword.cloud}}-Konsole an? Informationen hierzu finden Sie unter [Blockspeicherdatenträger anzeigen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage).
{: tip}

## Weitere Schritte
{: #next-step-viewing-block-storage-cli}

Erstellen Sie weitere Datenträger oder verwalten Sie die vorhandenen Blockspeicherdatenträger.

* [Blockspeicherdatenträger über die Befehlszeilenschnittstelle erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli)
* [Blockspeicherdatenträger über die Befehlszeilenschnittstelle verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
