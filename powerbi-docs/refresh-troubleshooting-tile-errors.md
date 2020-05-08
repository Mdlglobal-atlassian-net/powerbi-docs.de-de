---
title: Problembehandlung für Kachelfehler
description: Häufig in Power BI auftretende Fehler bei der Aktualisierung einer Kachel
author: maggiesMSFT
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 79f18faf56fba8afa85afd808f6faa1bd16811d8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79381144"
---
# <a name="troubleshooting-tile-errors"></a>Problembehandlung für Kachelfehler
Im Folgenden sind häufige Fehler, die Ihnen möglicherweise in Verbindung mit Kacheln begegnen, gemeinsam mit den entsprechenden Erklärungen aufgeführt.

> [!NOTE]
> Falls bei Ihnen ein Fehler auftritt, der hier nicht aufgelistet ist, und Ihnen Probleme verursacht, können Sie auf der [Communitywebsite](https://community.powerbi.com/) um Hilfe bitten oder ein [Support-Ticket](https://powerbi.microsoft.com/support/) erstellen.
> 
> 

## <a name="errors"></a>Fehler
**Unerwarteter Fehler bei Power BI beim Laden des Modells. Versuchen Sie es später erneut.**
Oder: **Das Datenmodell konnte nicht abgerufen werden. Wenden Sie sich an den Besitzer des Dashboards, um sicherzustellen, dass die Datenquellen und das Modell vorhanden sind und der Zugriff auf sie möglich ist.**

Es konnte nicht auf Ihre Daten zugegriffen werden, da die Datenquelle nicht erreichbar war. Dieses Problem kann auftreten, wenn die Datenquelle entfernt, umbenannt, verschoben oder offline geschaltet bzw. wenn ihre Berechtigungen geändert wurden. Überprüfen Sie, ob sich die Quelle noch an dem verwiesenen Speicherort befindet und ob Sie darauf zugreifen können. Wenn dies nicht die Ursache des Problems ist, liegt es möglicherweise an einer langsamen Quelle. Versuchen Sie es zu einem Zeitpunkt erneut, wenn die Auslastung der Quelle geringer ist. Wenn es sich um eine lokale Quelle handelt, erhalten Sie vom Datenquellenbesitzer möglicherweise weitere Informationen.

**Sie haben keine Berechtigung zum Anzeigen dieser Kachel oder zum Öffnen der Arbeitsmappe.**

Wenden Sie sich an den Besitzer des Dashboards, um sicherzustellen, dass die Datenquellen und das Modell vorhanden sind und Sie über Ihr Konto darauf zugreifen können.

**Power BI-Visuals wurden durch Ihren Administrator deaktiviert.**

Ihr Power BI-Administrator hat die Nutzung von Power BI-Visuals für Ihre Organisation oder Ihre Sicherheitsgruppe deaktiviert.
Sie können keine Power BI-Visuals von [Microsoft Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) verwenden und keine privaten Visuals aus einer Datei importieren. Sie können nur die vorgegebenen Visuals verwenden.


**Die Daten-Shapes müssen mindestens eine Gruppe oder Berechnung enthalten, die Daten ausgibt. Wenden Sie sich an den Besitzer des Dashboards.**

Es stehen keine Daten zur Anzeige zur Verfügung, da die Abfrage leer ist. Versuchen Sie, Ihrer Visualisierung einige Felder aus der Feldliste hinzuzufügen, und heften Sie sie erneut an.

**Die Daten können nicht angezeigt werden, da Power BI die Beziehung zwischen zwei oder mehr Feldern nicht bestimmen kann.**

Sie versuchen, zwei oder mehr Felder aus Tabellen zu verwenden, die nicht verknüpft sind. Sie müssen die nicht verknüpften Felder aus der Visualisierung und eine Beziehung zwischen den Tabellen erstellen. Anschließend können Sie die Felder wieder zum Visual hinzufügen. Dies kann in Power BI Desktop oder Power Pivot für Excel erfolgen. [Weitere Informationen](desktop-create-and-manage-relationships.md)

**Die Gruppen auf der Primärachse und der Sekundärachse überschneiden sich. Die Gruppen auf der Primärachse können nicht die gleichen Schlüssel wie die Gruppen auf der Sekundärachse aufweisen.**

Dies ist normalerweise ein vorübergehendes Problem. Es tritt i. d. R. auf, wenn Sie Gruppen von Zeilen in Spalten verschieben. In diesem Fall sollte der Fehler nicht mehr angezeigt werden, wenn Sie alle Gruppen verschoben haben. Wenn die Meldung weiterhin angezeigt wird, wechseln Sie zwischen Zeilen und Spalten bzw. der Achsenlegende, oder entfernen Sie Felder aus der Visualisierung.  

**Diese Visualisierung überschreitet die verfügbaren Ressourcen. Versuchen Sie, einen Filter anzuwenden, um die angezeigten Daten zu reduzieren.**

Ihre Visualisierung hat versucht, zu viele Daten abzufragen, sodass die Abfrage nicht mit den verfügbaren Ressourcen abgeschlossen werden konnte. Versuchen Sie, die Visualisierung zu filtern, um die Datenmenge im Ergebnis zu reduzieren.

**Die folgenden Felder können nicht identifiziert werden: {0}. Aktualisieren Sie die Visualisierung mit Feldern, die im Dataset vorhanden sind.**

Das Feld wurde möglicherweise gelöscht oder umbenannt. Entfernen Sie das fehlerhafte Feld aus der Visualisierung, fügen Sie ein anderes Feld hinzu, und heften Sie sie erneut an.

**Die Daten für diese Visualisierung konnten nicht abgerufen werden. Versuchen Sie es später erneut.**

Dies ist normalerweise ein vorübergehendes Problem. Wenn Sie es später erneut versuchen und diese Meldung weiterhin angezeigt wird, wenden Sie sich an den Support.

**Nach dem Aktivieren der einmaligen Anmeldung (Single Sign-On, SSO) zeigen Kacheln weiterhin ungefilterte Daten an.**

Dies kann der Fall sein, wenn das zugrunde liegende Dataset so konfiguriert ist, dass der DirectQuery-Modus oder eine Liveverbindung zu Analysis Services über ein lokales Datengateway verwendet wird. In diesem Fall zeigen die Kacheln weiterhin die ungefilterten Daten an, nachdem SSO für die Datenquelle aktiviert wurde, bis die nächste Aktualisierung der Kachel ansteht. Bei der nächsten Kachelaktualisierung verwendet Power BI SSO gemäß der Konfiguration, und die Kacheln zeigen die gefilterten Daten entsprechend der Benutzeridentität an. 

Wenn Sie die gefilterten Daten sofort anzeigen möchten, können Sie eine Kachelaktualisierung auch erzwingen, indem Sie auf **Weitere Optionen** (...) oben rechts in einem Dashboard und dann auf **Dashboardkacheln aktualisieren** klicken.

Als Besitzer des Datasets können Sie auch die Aktualisierungshäufigkeit der Kachel ändern und diese auf 15 Minuten festlegen, um die Kachelaktualisierung zu beschleunigen. Wählen Sie rechts oben im Power BI-Dienst das Zahnradsymbol und dann **Einstellungen** aus. Klicken Sie auf der Seite **Einstellungen** auf die Registerkarte **Datasets**. Erweitern Sie **Geplante Cache Aktualisierung**, und ändern Sie die **Aktualisierungshäufigkeit**. Stellen Sie sicher, dass Sie die Konfiguration auf die ursprüngliche Aktualisierungshäufigkeit zurücksetzen, nachdem Power BI die nächste Kachelaktualisierung durchgeführt hat.

> [!NOTE]
> Der Abschnitt **Geplante Cacheaktualisierung** ist nur für Datasets im DirectQuery-/Liveverbindungsmodus verfügbar. Für Datasets im Importmodus ist keine separate Kachelaktualisierung erforderlich, da die Kacheln während der nächsten geplanten Datenaktualisierung automatisch aktualisiert werden.

## <a name="contact-support"></a>Support kontaktieren
Wenn weiterhin Probleme auftreten, wenden Sie sich an den [Support](https://support.powerbi.com), um dem Problem auf den Grund zu gehen.

## <a name="next-steps"></a>Nächste Schritte
[Problembehandlung beim lokalen Datengateway](service-gateway-onprem-tshoot.md)  
[Problembehandlung in Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

