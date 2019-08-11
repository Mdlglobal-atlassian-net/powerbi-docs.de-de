---
title: Einführung in Dashboards für Power BI-Designer
description: Dashboards sind ein zentrales Feature des Power BI-Diensts. Sie bestehen aus einer einzelnen Seite (häufig als Canvas bezeichnet), auf der mithilfe von Visualisierungen Informationen veranschaulicht werden.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 7ee083de9800b55c4f7d998a113c1a63df112b7b
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68624021"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Einführung in Dashboards für Power BI-Designer

Ein Power BI-*Dashboard* ist eine einzelne Seite (häufig als Canvas bezeichnet), auf der mithilfe von Visualisierungen Informationen veranschaulicht werden. Wegen der Beschränkung auf eine Seite erkennen Sie ein gut gestaltetes Dashboard daran, dass die Informationsdarstellung auf ihre wichtigsten Punkte verdichtet ist. Leser können verwandte Berichte anzeigen, um Details zu erfahren.

![Dashboard](media/service-dashboards/power-bi-dashboard2.png)

Dashboards sind ein reines Feature des Power BI-Diensts. Sie sind in Power BI Desktop nicht verfügbar. Zwar können Sie auf mobilen Geräten keine Dashboards erstellen, doch können Sie sie [anzeigen und freigeben](mobile-apps-view-dashboard.md).

## <a name="dashboard-basics"></a>Dashboard-Grundlagen 

Die Visualisierungen auf dem Dashboard heißen *Kacheln*. Kacheln werden aus Berichten an ein Dashboard *angeheftet*. Wenn Sie noch nicht mit Power BI vertraut sind, können Sie sich mithilfe des Artikels [Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md) eine gute Grundlage schaffen.

> [!IMPORTANT]
> Sie benötigen eine [Power BI Pro](service-free-vs-pro.md)-Lizenz, um Dashboards zu erstellen.

Die Visualisierungen eines Dashboards stammen aus Berichten. Jeder Bericht basiert auf einem Dataset. Sie können sich ein Dashboard als Fenster zu den zugrunde liegenden Berichten und Datasets vorstellen. Wenn Sie eine Visualisierung auswählen, gelangen Sie zu dem Bericht (und damit dem Dataset), auf dem sie basiert.

![Diagramm, das die Beziehungen zwischen Dashboards, Berichten und Datasets anzeigt](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vorteile von Dashboards
Mit Dashboards können Sie die Entwicklung Ihres Geschäfts verfolgen und die wichtigsten Metriken immer im Auge behalten. Jede Visualisierung eines Dashboards kann auf einem oder vielen Datasets, auf einem einzelnen Bericht oder zahllosen Berichten basieren. Ein Dashboard fasst lokale und Clouddaten zusammen und bietet eine konsolidierte Ansicht – unabhängig vom Speicherort der Daten.

Ein Dashboard ist nicht nur schön anzusehen. Es ist ausgesprochen interaktiv, und die Kacheln aktualisieren sich automatisch, wenn sich die zugrunde liegenden Daten ändern.

## <a name="dashboards-versus-reports"></a>Vergleich: Dashboards und Berichte
[Berichte](service-reports.md) und Dashboards sehen ähnlich aus, da sie beide Canvases sind, die mit Visualisierungen gefüllt sind. Es gibt jedoch wesentliche Unterschiede, wie in der folgenden Tabelle zu sehen ist.

| **Eigenschaften** | **Dashboards** | **Berichte** |
| --- | --- | --- |
| Pages |Eine Seite |Eine oder mehrere Seiten |
| Datenquellen |Ein oder mehrere Berichte und ein oder mehrere Datasets pro Dashboard |Ein Dataset pro Bericht |
| In Power BI Desktop verfügbar |Nein | Ja. Berichte können in Power BI Desktop erstellt und angezeigt werden |
| Abonnieren |Ja. Dashboards können abonniert werden. |Ja. Kann eine Berichtsseite abonnieren. |
| Filter |Nein. Keine Filter, keine Slices |Ja. Viele Filter, Hervorhebungen und Slices |
| Empfohlen |Ja. Kann ein Dashboard als Ihr *Ausgewähltes* Dashboard festlegen |Nein |
| Favorit | Ja. Kann mehrere Dashboards als *Favoriten* festlegen. | Ja. Kann mehrere Berichte als *Favoriten* festlegen.
| Benachrichtigungen festlegen |Ja. Unter bestimmten Umständen für Dashboardkacheln verfügbar |Nein |
| Abfragen in natürlicher Sprache (Q&A) |Ja | Ja, vorausgesetzt, Sie verfügen über Bearbeitungsberechtigungen für den Bericht und das zugrunde liegende Dataset. |
| Zugrunde liegende Dataset-Tabellen und Felder sichtbar |Nein. Kann Daten exportieren, Tabellen und Felder sind im Dashboard aber nicht sichtbar. |Ja |


## <a name="next-steps"></a>Nächste Schritte
* Machen Sie sich mit Dashboards vertraut, indem Sie sich eine Tour durch eines unserer [Beispiel-Dashboards](sample-tutorial-connect-to-the-samples.md) ansehen.
* Wichtige Informationen über [Dashboardkacheln](service-dashboard-tiles.md)
* Sie möchten eine bestimmte Dashboardkachel im Auge behalten und eine E-Mail erhalten, wenn ein bestimmter Grenzwert erreicht wird? [Erstellen einer Warnung auf einer Kachel](service-set-data-alerts.md).
* Mit [Power BI Q&A](power-bi-tutorial-q-and-a.md) können Sie Fragen zu Ihren Daten stellen und erhalten eine Antwort in Form einer Visualisierung.
