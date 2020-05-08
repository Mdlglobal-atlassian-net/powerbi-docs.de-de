---
title: Einstellungen für die Seitenanzeige in einem Power BI-Bericht
description: Einstellungen für Seitenanzeige und Seitenansicht für Berichte
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 6aefe879e6d5871c8f88ac15407038aa600bf980
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75762506"
---
# <a name="apply-page-display-settings-in-a-power-bi-report"></a>Anwenden von Einstellungen für die Seitenanzeige in einem Power BI-Bericht
Wir wissen, wie wichtig es ist, dass das Layout des Berichts perfekt ist. Das ist in manchen Fällen jedoch schwierig, da Sie und Ihre Kollegen die Berichte möglicherweise auf Bildschirmen mit unterschiedliche Seitenverhältnissen und Größen anzeigen. 

Die Standardeinstellung für die Anzeige ist **An Seite anpassen** und die Standardgröße ist **16:9**. Wenn Sie ein anderes Seitenverhältnis nutzen oder den Bericht auf eine andere Weise anpassen möchten, stehen Ihnen zwei Tools zur Verfügung: die Einstellungen für die ***Seitenansicht*** und die ***Seitengröße***.


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>Informationen zu den Einstellungen für die Seitenansicht im Power BI-Dienst und in Power BI Desktop
Einstellungen für die Seitenansicht sind sowohl im Power BI-Dienst als auch in Power BI Desktop verfügbar, die Benutzeroberflächen unterscheiden sich aber leicht. In den folgenden Abschnitten wird erläutert, wo sich die Einstellungen für die Seitenansicht in den verschiedenen Power BI-Tools befinden.

### <a name="in-power-bi-desktop"></a>Power BI Desktop
Wählen Sie in der Berichtsansicht die Registerkarte **Ansicht** aus, um die Einstellungen für die Seitenansicht sowie für das Telefonlayout zu öffnen.

  ![Einstellungen für die Desktopseitenansicht](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>Power BI-Dienst („app.powerbi.com“)
Öffnen Sie im Power BI-Dienst einen Bericht, und wählen Sie in der oberen linken Menüleiste **Ansicht** aus.

![Einstellungen für die Dienstseitenansicht](media/power-bi-report-display-settings/power-bi-change-page-view.png)

Die Einstellungen für die Seitenansicht stehen in der [Leseansicht und der Bearbeitungsansicht](consumer/end-user-reading-view.md) zur Verfügung. In der Bearbeitungsansicht kann der Besitzer eines Berichts einzelnen Berichtsseiten eine Seitenansichtseinstellung zuweisen; diese Einstellungen werden mit dem Bericht gespeichert. Wenn ein Kollege den Bericht in der Leseansicht öffnet, werden ihm die Berichtsseiten mit den Einstellungen des Besitzers angezeigt. In der Leseansicht können die Kollegen *einige* der Einstellungen für die **Seitenansicht** ändern. Die Änderungen werden aber nicht gespeichert, wenn sie den Bericht schließen.

## <a name="page-view-settings"></a>Seitenansichtseinstellungen
Mit der ersten Gruppe von Einstellungen für die Seitenansicht wird die Anzeige der Berichtsseite in Relation zum Browserfenster angepasst. Sie können zwischen folgenden Einstellungen wählen:

* **An Seite anpassen** (Standard): Inhalte werden für die beste Anpassung an die Seitengröße skaliert.
* **An Breite anpassen**: Inhalte werden für die Anpassung an die Seitenbreite skaliert.
* **Tatsächliche Größe**: Inhalte werden in voller Größe angezeigt.

Die zweite Gruppe von Einstellungen für die Seitenansicht steuert die Positionierung von Objekten im Zeichenbereich des Berichts. Sie können zwischen folgenden Einstellungen wählen:

* **Gitternetzlinien anzeigen**: Hiermit werden Gitternetzlinien eingeblendet, damit Sie Objekte leichter auf dem Zeichenbereich des Berichts positionieren können.
* **Am Raster ausrichten**: In Kombination mit **Gitternetzlinien anzeigen** können Sie hiermit Objekte im Zeichenbereich des Berichts genau positionieren und ausrichten. 
* **Objekte sperren**: Hiermit werden alle Objekte im Zeichenbereich gesperrt und können nicht mehr verschoben oder in der Größe geändert werden.
* **Auswahlbereich**: Im **Auswahlbereich** werden alle Objekte im Zeichenbereich aufgelistet. Sie können entscheiden, welche Objekte angezeigt und welche ausgeblendet werden sollen.

    ![Auswahlbereich](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Seitengrößeeinstellungen
![Seitengrößeeinstellungen ändern](media/power-bi-report-display-settings/power-bi-page-size.png)

Die Einstellungen für die **Seitengröße** sind nur für den Besitzer eines Berichts verfügbar. Im Power BI-Dienst („app.powerbi.com“) müssen Sie hierzu den Bericht in der [Bearbeitungsansicht](consumer/end-user-reading-view.md) öffnen können. Mit den Einstellungen für die **Seitengröße** im Bereich **Visualisierungen** können Sie das Seitenverhältnis und die tatsächliche Größe (in Pixel) des Zeichenbereichs festlegen:   

* 4:3-Seitenverhältnis
* 16:9-Seitenverhältnis (Standard)
* Letter
* Benutzerdefiniert (Höhe und Breite in Pixel)

## <a name="next-steps"></a>Nächste Schritte
[Berichtsansicht in Power BI Desktop](desktop-report-view.md)

[Ändern der Einstellungen für Seitenansicht und Seitengröße in Ihren eigenen Power BI-Berichten](consumer/end-user-report-view.md)

Erfahren Sie mehr über [Berichte in Power BI](consumer/end-user-reports.md).

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

