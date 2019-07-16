---

copyright:
  years: 2019
lastupdated: "2018-06-17"

keywords: block storage, IBM Cloud, VPC, virtual private cloud, volume, data storage, troubleshooting, troubleshoot


subcollection: vpc-on-classic-block-storage


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Fehlerbehebung für Blockspeicher
{: #troubleshoot}

Beim Erstellen und Verwalten von Blockspeicher können Probleme auftreten. Diese Probleme oder Fehler können in vielen Fällen durch einige wenige einfache Schritte behoben werden. Probleme, Symptome, wahrscheinliche Ursachen und Lösungen werden in den folgenden Abschnitten beschrieben.{:shortdesc}

## Ein Datenträger kann in einer angegebenen Region nicht abgerufen werden.
{: #troubleshoot-topic-1}

Informationen zu Blockspeicherdatenträgern konnten für eine bestimmte Region nicht abgerufen werden.
{: tsSymptoms}

Es kann eine der folgenden Ursachen vorliegen:

* Der Datenträgername oder andere erforderliche Datenträgerangaben fehlen in der Benutzerschnittstellen- oder Befehlszeilenschnittstellenausgabe.
* Möglicherweise versuchen Sie, auf einen Datenträger in einer anderen Region als Ihrer Region zuzugreifen.
* Möglicherweise versuchen Sie, auf einen Datenträger der Generation 2 zuzugreifen.
{: tsCauses}

Stellen Sie sicher, dass die Zuordnung des Datenträgers zu einer virtuellen Serverinstanz nicht aufgehoben und der Datenträger gelöscht wurde. Suchen Sie in der Liste der virtuellen Serverinstanzen nach der Instanz, der Sie den Datenträger zuletzt zugeordnet hatten:

1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/vpc){: external} zu **Menüsymbol ![Menüsymbol](../../icons/icon_hamburger.svg) > Datenverarbeitung > Virtuelle Serverinstanzen für VPC**.

1. Wählen Sie eine virtuelle Serverinstanz in der Liste der virtuellen Server aus.

Wenn der Datenträger nicht wie erwartet zugeordnet ist und nicht in der Liste der Datenträger angezeigt wird, wurde er wahrscheinlich gelöscht. Da beim Löschen eines Datenträgers die zugehörigen Daten vollständig entfernt werden, ist eine Wiederherstellung nicht möglich.  

Überprüfen Sie bei Verwendung der Befehlszeilenschnittstelle, ob Sie die korrekte Befehlssyntax für das Anzeigen von Datenträgern verwendet haben. Weitere Informationen hierzu finden Sie unter [Alle Blockspeicherdatenträger über die Befehlszeilenschnittstelle anzeigen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-attaching-block-storage-cli). Stellen Sie sicher, dass Sie die richtige Ressourcengruppe oder -zone angegeben haben.
{: tsResolve}

## Ein Datenträger kann nicht über den zugehörigen Namen oder die ID gelöscht werden
{: #troubleshoot-topic-2}

Ein Blockspeicherdatenträger kann nicht über den zugehörigen Namen oder die ID gelöscht werden.
{: tsSymptoms}

Datenträgername und -ID werden nicht akzeptiert.
{: tsCauses}

Stellen Sie sicher, dass der Datenträgername bzw. die Datenträger-ID korrekt ist und dass der Datenträger nicht einer virtuellen Serverinstanz zugeordnet ist. Stellen Sie außerdem sicher, dass der Datenträger nicht den Status "Anstehend" aufweist.
{: tsResolve}
