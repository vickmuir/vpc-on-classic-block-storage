---

copyright:
  years: 2019
lastupdated: "2019-07-01"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, CLI, block storage volume, volume, volume attachment, virtual server instance, instance

subcollection: vpc-on-classic-block-storage


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Blockspeicherdatenträger über die Befehlszeilenschnittstelle zuordnen
{: #attaching-block-storage-cli}

Beim Zuordnen von Datenträgern wird ein {{site.data.keyword.block_storage_is_short}}-Datenträger mit einer virtuellen Serverinstanz verbunden. Jede Instanz kann mehrere [Datenträgerzuordnungen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage#vol-attach-limits) aufweisen, bei einer Datenträgerzuordnung wird jedoch jeweils nur ein einziger Datenträger zu einer einzelnen Instanz zugeordnet.
{:shortdesc}

## Vorbereitungen
{: #before-attaching-block-storage-cli}

1. Stellen Sie sicher, dass Sie die folgenden Plug-ins für die Befehlszeilenschnittstelle heruntergeladen, installiert und initialisiert haben:
    * {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle
    * Infrastrukturservice-Plug-in

   Weitere Informationen finden Sie in den [Referenzinformationen zur {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle für VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference). 
   
   Wenn Sie das VPC-Infrastruktur-Plug-in zum ersten Mal installieren, müssen Sie für die Zielgeneration 'gen 1' festlegen: `ibmcloud is target --gen 1`.
   {:important}
   
2. Stellen Sie sicher, dass bereits eine [{{site.data.keyword.vpc_short}}-Instanz erstellt](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started) wurde. 

## Blockspeicherdatenträger über die Befehlszeilenschnittstelle zuordnen
{: #attach-block-storage-cli}

Führen Sie zum Zuordnen eines Datenträgers zu einer virtuellen Serverinstanz in der aktuellen Ressourcengruppe den folgenden Befehl aus.

```bash
ibmcloud is instance-volume-attachment-add NAME INSTANZ-ID DATENTRÄGER-ID [--auto-delete true | false] [--json]
```

`NAME` ist der Name, den Sie für die Datenträgerzuordnung angeben, INSTANZ-ID die ID der virtuellen Serverinstanz.

`DATENTRÄGER-ID` gibt den Datenträger an, der zugeordnet werden soll.

Geben Sie `--auto-delete true` an, wenn der Datenträger automatisch gelöscht werden soll, sobald die virtuelle Serverinstanz gelöscht wird.

Mit dem Befehl `ibmcloud is instances` können Sie eine Liste der verfügbaren virtuellen Serverinstanzen anzeigen.

Beispiel:

```bash
$ ibmcloud is instances
Listing instances under account my-account-01 as user rtuser1@mycompany.com...
ID                                     Name                  Address          Profile   Image                            Created        Status     VPC                               Zone         Resource Group
916e3ccf-b3af-47a5-b549-c9a3b9815559   instance-test2        192.xxx.xx.xx    -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc1(974e258e-.)    us-south-1   -
b762f064-26a6-4ffe-bfe4-4a21d92effaf   instance-test1        192.xxx.xx.x     -         ubuntu-16.04-amd64(7eb4e35b-.)   4 hours ago    running    function-test-vpc2(974e258e-.)    us-south-1   -
ad0ade52-0533-4dc6-a145-f1ad6d5bee2c   vsi-09202             192.xxx.xxx.xx   -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -
e6353eba-c407-4406-b9f6-c50ee1da8d83   vsi-09201             192.xxx.xxx.xxx  -         ubuntu-16.04-amd64(7eb4e35b-.)   5 hours ago    running    vpnaas-test1(2467b0fa-.)          us-south-1   -

```
{: screen}

## Details zu einer virtuellen Serverinstanz zugeordneten Datenträgern anzeigen
{: #show-details-attached-vol}

Nach dem Zuordnen eines Datenträgers können Sie Details anzeigen, indem Sie die Instanz-ID und die ID der Datenträgerzuordnung im Befehl `instance-volume-attachment` angeben.

```bash
ibmcloud is instance-volume-attachment INSTANZ-ID DATENTRÄGERZUORDNUNGS-ID [--json]
```

## Datenträgerzuordnungen einer Serverinstanz auflisten

Geben Sie zum Anzeigen der Datenträgerzuordnungen einer Instanz den Befehl `instance-volume-attachments` mit der jeweiligen Instanz-ID ein.

```bash
ibmcloud is instance-volume-attachments INSTANZ-ID [--json]
```

Wenn Sie lieber mit der {{site.data.keyword.cloud}}-Konsole arbeiten, finden Sie unter [Blockspeicherdatenträger zuordnen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage) nähere Informationen zum Zuordnen von Datenträgern in der Konsole.
{:tip}

## JSON für Datenträgerzuordnung erstellen
{: #volume_attachment_json}

Wenn Sie eine virtuelle Serverinstanz über die Befehlszeilenschnittstelle bereitstellen und bei diesem Prozess einen Blockspeicherdatenträger erstellen, müssen Sie mit JSON eine Datenträgerzuordnung angeben. Der in dem Befehl oder als Datei angegebene JSON-Code für die Datenträgerzuordnung definiert die Datenträgerparameter. Wenn Sie [eine Instanz erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) und den Parameter `-- volume-attach` angeben, geben Sie den JSON-Code für den Datenträger an. Geben Sie z. B. Folgendes an: `--volume-attach @/Users/myname/myvolume-attachment_create.json`.

Im Folgenden finden Sie eine JSON-Beispieldatei für Datenträgerzuordnung, über die ein angepasster Datenträger definiert wird:

```
[
    {
        "name": "myvolume-attachment",
        "delete_volume_on_instance_delete": true,
        "volume": {
            "name": "myvolume",
            "capacity": 100,
            "iops": 1000,
            "profile": {
                "name": "custom"
            }
        }
    }
]
```
{: screen}

## Weitere Schritte
{: #next-step-attaching-block-storage-cli}

Erstellen Sie zusätzliche Datenträger und verwalten Sie vorhandene Datenträger.  Siehe dazu die folgenden Informationen.

* [Blockspeicherdatenträger über die Befehlszeilenschnittstelle erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli#create-vol-cli)
* [Blockspeicherdatenträger über die Befehlszeilenschnittstelle verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage-cli)
