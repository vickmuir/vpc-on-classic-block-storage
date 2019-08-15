---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: block storage, getting started, IBM Cloud, VPC, virtual private cloud, IBM CLoud, volume, data storage, classic, virtual server

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
{:shortdesc: .shortdesc}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# {{site.data.keyword.block_storage_is_short}} - Einführung
{: #getting-started}

Das vorliegende Lernprogramm hilft Ihnen beim Erstellen von {{site.data.keyword.block_storage_is_short}}-Datenträgern in Virtual Private Cloud.
{: .shortdesc}

## Vorbereitungen
{: #block-storage-before-you-begin}

Überprüfen Sie zunächst, welche Abschnitte bei Ihrer Implementierung hilfreich sein können. Sind Sie mit {{site.data.keyword.cloud}} und {{site.data.keyword.block_storage_is_short}} noch nicht vertraut? Die folgenden Informationen sind möglicherweise hilfreich:

* [{{site.data.keyword.vpc_full}}](https://www.ibm.com/cloud/vpc){: external}
* [Informationen zu Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)

Melden Sie sich für ein {{site.data.keyword.cloud_notm}}-Konto an. Weitere Informationen hierzu finden Sie unter [Für {{site.data.keyword.cloud_notm}} anmelden](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}.

## Schritt 1 - Speicherbedarf ermitteln
{: #determine-storage-requirements}

Werden allgemeine Workloads mit geringem Speicherbedarf ausgeführt? Oder handelt es sich bei Ihren Workloads um ein-/ausgabeintensive Workloads, die eine höhere Kapazität und Leistung erfordern? Nähere Informationen zum Ermitteln von Kapazität und Leistung finden Sie unter [Blockspeicherkapazität und -leistung](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-capacity-performance). Unter [Profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles) erfahren Sie, welche IOPS-Profiloption Ihrem Speicherbedarf am besten entspricht. 

Erstellen Sie auch eine virtuelle Serverinstanz? Weitere Informationen finden Sie unter [Zusammenhang zwischen Profilen virtueller Server und Speicherprofilen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#vsi-profiles-relate-to-storage).

## Schritt 2 - Größe und Preis für Ihren Blockspeicher
{: #size-price-block-storage}

Wählen Sie ein [IOPS-Tier-Profil](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) für Ihren Blockspeicherdatenträger aus.  Wenn Sie über genau definierte Leistungsanforderungen verfügen, die keinem vordefinierten IOPS-Tier entsprechen, wählen Sie bei Bedarf ein [angepasstes IOPS-Profil](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#custom) aus. 

Nachdem Sie die Größe und Leistung für Ihre Blockspeicherdatenträger ausgewählt haben, lesen Sie die Informationen zur [Preisstruktur](/docs/vpc-on-classic?topic=vpc-on-classic-block-storage-pricing), um sich über die Preisgestaltung Ihrer Datenträger und die Rechnungsstellung zu informieren.

## Schritt 3 - Melden Sie sich in Ihrem {{site.data.keyword.cloud_notm}}-Konto
{: block-storage-log-into-ibm-account}

Greifen Sie auf das {{site.data.keyword.block_storage_is_short}}-Bestellformular im [{{site.data.keyword.cloud_notm}}-Katalog](https://{DomainName}/catalog){: external} zu. Verwenden Sie Ihre IBMid und das zugehörige Kennwort.

## Schritt 4 (optional) - Zugriff auf {{site.data.keyword.vpc_short}} überprüfen

Wenn Sie einen Datenträger in Virtual Private Cloud erstellen möchten, müssen Sie zuerst [eine VPC-Instanz erstellen](/docs/vpc-on-classic?topic=vpc-on-classic-creating-a-vpc-using-the-ibm-cloud-console). Überspringen Sie diesen Schritt, wenn Sie einen eigenständigen Datenträger außerhalb von VPC erstellen möchten. Sie können später den Zugriff auf {{site.data.keyword.vpc_short}} anfordern, um auf eine Instanz zuzugreifen und einen von Ihnen separat erstellten Blockspeicherdatenträger zuzuordnen. Weitere Informationen zu {{site.data.keyword.vpc_short}} finden Sie im [Einführungslernprogramm für VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Schritt 5 - Blockspeicherdatenträger erstellen

Beginnen Sie mit dem Erstellen von Datenträgern in der [{{site.data.keyword.cloud_notm}}-Konsole (Benutzerschnittstelle)](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage) oder mithilfe der [Befehlszeilenschnittstelle](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage-cli), oder verwenden Sie die [{{site.data.keyword.vpc_short}}-API](https://{DomainName}/apidocs/vpc-on-classic#create-a-volume){: external}. Weitere Informationen zur Verwendung der IBM Cloud Developer-Tools für die Installation der IBM Cloud-Befehlszeilenschnittstelle finden Sie in der [Einführung zu IBM Cloud Developer-Tools](/docs/cli?topic=cloud-cli-getting-started).

## Weitere Schritte
{: #next-step-block-storage-getting-started}

Nachdem Sie Blockspeicher erstellt haben, können Sie sich mit weiteren Optionen vertraut machen:

* [Details zum Datenträger anzeigen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-viewing-block-storage)
* [Blockspeicherdatenträger verwalten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-managing-block-storage#managing-block-storage)
