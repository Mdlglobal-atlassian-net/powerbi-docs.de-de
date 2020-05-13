---
title: Einführung in organisationsbezogene Inhaltspakete in Power BI
description: Erfahren Sie, wie Sie Ihre Dashboards, Berichte, Excel-Arbeitsmappen und Datasets in organisationsbezogene Inhaltspakete packen, die Sie für Ihre Kollegen freigeben können.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ad60e65406ee69bed4e544486c955765203ddc5c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347997"
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Einführung in organisationsbezogene Inhaltspakete in Power BI
> [!NOTE]
> Sie können in den neuen Arbeitsbereichsumgebungen keine organisationsbezogenen Inhaltspakete erstellen oder installieren. Führen Sie jetzt ein Upgrade durch, und wandeln Sie Ihre Inhaltspakete in Apps um, falls Sie dies noch nicht getan haben. Erfahren Sie [mehr über die neuen Arbeitsbereiche](service-create-the-new-workspaces.md).
> 

Verteilen Sie regelmäßig Berichte per E-Mail an Ihr Team? Probieren Sie diese Alternative aus: Packen Sie Ihre Dashboards, Berichte, Excel-Arbeitsmappen und Datasets, und veröffentlichen Sie sie für Ihr Team als *organisationsbezogenes Inhaltspaket*. Alle von Ihnen erstellten Inhaltspakete kann Ihr Team leicht in AppSource finden. Da Inhaltspakete Teil von Power BI sind, nutzen sie alle Features von Power BI, einschließlich interaktiver Untersuchung von Daten, neuer Visualisierungen, Fragen und Antworten, Integration mit anderen Datenquellen, Aktualisierung von Daten und mehr.

![](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

Das Erstellen von Inhaltspaketen unterscheidet sich vom Freigeben von Dashboards oder dem gemeinsamen Bearbeiten in einem Arbeitsbereich. Lesen Sie den Artikel [Wie kann ich Dashboards und Berichte freigeben?](service-how-to-collaborate-distribute-dashboards-reports.md), um die beste Option für Ihre Situation zu ermitteln. 

In AppSource können Sie die Inhaltspakete durchsuchen, die für die gesamte Organisation, für Verteiler- oder Sicherheitsgruppen sowie für [Office 365-Gruppen, deren Mitglied Sie sind](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9), veröffentlicht wurden. Wenn Sie kein Mitglied einer bestimmten Gruppe sind, werden Ihnen die Inhaltspakete nicht angezeigt, die für diese Gruppe freigegeben sind. Der schreibgeschützte Zugriff auf die Inhaltspaketdaten, Berichte, Arbeitsmappen und Dashboards ist für alle Mitglieder der Gruppe identisch (sofern es sich nicht um eine SQL Server Analysis Services (SSAS)-Datenquelle handelt, bei der die Berechtigungen mit der Datenquelle geerbt werden).

Die Dashboards, Berichte und Excel-Arbeitsmappen sind schreibgeschützt. Sie können die Berichte und Dashboards jedoch kopieren und als Ausgangspunkt für die Erstellung einer eigenen personalisierten Version des Inhaltspakets verwenden.

> [!NOTE]
> Organisationsbezogene Inhaltspakete sind nur verfügbar, wenn Sie und Ihre Kollegen mit [Power BI Pro-Lizenzen](../fundamentals/service-features-license-type.md) arbeiten.
> 
> 

## <a name="what-is-appsource"></a>Was ist *AppSource*?
Durch Veröffentlichen eines organisationsbezogenen Inhaltspakets wird dieses zu AppSource hinzugefügt.  Dieses zentrale Repository vereinfacht Mitgliedern das Durchsuchen und Ermitteln von Dashboards, Berichten und Datasets, die für sie veröffentlicht wurden.  

* Wählen Sie zum Anzeigen von AppSource **Daten abrufen** > **Meine Organisation** > **Abrufen** aus.

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>Lebenszyklus eines organisationsbezogenen Inhaltspakets
Jeder Power BI Pro-Benutzer kann organisationsbezogene Inhaltspakete erstellen, veröffentlichen und auf sie zugreifen. Nur der Ersteller des Inhaltspakets kann die Arbeitsmappe und das Dataset ändern, deren Aktualisierung planen und sie löschen.

Der Lebenszyklus sieht etwa wie folgt aus:

1. Nate erstellt in Power BI Pro ein Inhaltspaket und veröffentlicht es für die Verteilergruppe „Marketing“. Die Einstellungen für die Aktualisierung werden mit dem Dataset geerbt und können nur von Nate geändert werden.
   
   > [!NOTE]
   > Wenn Nate das Inhaltspaket von einem [Power BI-Arbeitsbereich](service-create-distribute-apps.md) aus erstellt, dem Nate angehört, können andere Mitglieder dieses Power BI-Arbeitsbereichs auch dann Besitzer des Inhaltspakets werden, wenn Nate den Arbeitsbereich verlässt.
   > 
   > 
2. Nate sendet eine E-Mail an die Verteilergruppe, in der er Informationen über das neue Inhaltspaket mitteilt.
3. In Power BI Pro sucht Jane, ein Mitglied der Verteilergruppe „Marketing“, nach einem Inhaltspaket und stellt eine Verbindung mit dem Inhaltspaket in AppSource her. Jane verfügt jetzt über eine schreibgeschützte Kopie. Jane weiß, dass es sich um eine schreibgeschützte Kopie handelt, da im Navigationsbereich links neben dem Dashboard- und Berichtsnamen ein Freigabesymbol angezeigt wird. Und wenn Jane das Dashboard auswählt, weist ein Schlosssymbol darauf hin, dass sie sich das Dashboard eines Inhaltspakets ansieht. 
4. Angenommen, Jane entschließt sich, es anzupassen. Jane verfügt jetzt über ihre eigene Kopie des Dashboards und der Berichte. Janes Arbeit wirkt sich nicht auf die Quelle, das ursprüngliche Inhaltspaket oder auf andere Mitglieder der Verteilergruppe aus. Sie arbeiten jetzt jeweils an ihrer eigenen Kopie von Dashboard und Bericht.
5. Nate nimmt Aktualisierungen am Dashboard vor. Sobald es fertig ist, veröffentlicht er eine neue Version des Inhaltspakets.
   
   * Julio, Mitglied einer anderen Verteilergruppe, hat das ursprüngliche Inhaltspaket nicht angepasst. Die neuen Änderungen werden automatisch auf Julios Version des Inhaltspakets angewendet.  
   * Jane hat das Inhaltspaket angepasst. Jane erhält dann eine Benachrichtigung, dass es eine neue Version gibt.  Jane kann zu AppSource navigieren und das aktualisierte Inhaltspaket abrufen, ohne dass ihre personalisierte Version verloren geht. Jane verfügen jetzt über zwei Versionen: die personalisierte Version und das aktualisierte Inhaltspaket.
6. Angenommen, Nate ändert die Sicherheitseinstellungen. Julio und Jane haben keinen Zugriff mehr auf den Inhalt. Oder sie wurden aus der Verteilergruppe „Marketing“ entfernt.
   
   * Julio hat das ursprüngliche Inhaltspaket nicht angepasst, weshalb der Inhalt automatisch entfernt wird. 
   * Jane hat das Inhaltspaket angepasst. Wenn Jane das Dashboard das nächste Mal öffnet, sind alle Kacheln aus dem ursprünglichen Inhaltspaket nicht mehr da, doch die Kacheln, die sie aus anderen Berichten (die Jane weiter verwenden darf) angeheftet hat, werden weiterhin angezeigt. Die zugehörigen Berichte und das Dataset sind nicht mehr verfügbar (und werden nicht in ihrem Navigationsbereich angezeigt).
7. Oder Nate löscht das Inhaltspaket.
   
   * Julio hat das ursprüngliche Inhaltspaket nicht angepasst, weshalb der Inhalt automatisch entfernt wird. 
   * Jane hat das Inhaltspaket angepasst. Wenn Jane das Dashboard das nächste Mal öffnet, sind alle Kacheln aus dem ursprünglichen Inhaltspaket nicht mehr da, doch die Kacheln, die sie aus anderen Berichten angeheftet hat, werden weiterhin angezeigt. Die zugehörigen Berichte und das Dataset sind nicht mehr verfügbar (und werden nicht in ihrem Navigationsbereich angezeigt).

## <a name="data-security"></a>Datensicherheit
Alle Mitglieder der Verteilergruppe verfügen über dieselben Berechtigungen für die Daten wie der Ersteller des Inhaltspakets. Die einzige Ausnahme hierbei sind lokale tabellarische SSAS (SQL Server Analysis Services)-Datasets. Da die Berichte und Dashboards eine Liveverbindung mit dem lokalen SSAS-Modell herstellen, wird anhand der Anmeldeinformationen der einzelnen Verteilergruppenmitglieder bestimmt, auf welche Daten das jeweilige Mitglied zugreifen darf.

## <a name="next-steps"></a>Weitere Schritte
* [Erstellen und Veröffentlichen von organisationsbezogenen Inhaltspaketen](service-organizational-content-pack-create-and-publish.md)
* [Erstellen und Verteilen einer App in Power BI](service-create-distribute-apps.md) 
* [Grundlegende Konzepte für Designer im Power BI-Dienst](../fundamentals/service-basic-concepts.md)
* Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
