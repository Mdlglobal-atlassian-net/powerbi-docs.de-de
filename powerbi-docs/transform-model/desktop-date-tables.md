---
title: Festlegen und Verwenden von Datumstabellen in Power BI Desktop
description: Erfahren Sie, wie Sie in Power BI Desktop eine Tabelle als Datumstabelle festlegen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 6456d6126245ac6416dd7f50e705a0c731d98623
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83325826"
---
# <a name="set-and-use-date-tables-in-power-bi-desktop"></a>Festlegen und Verwenden von Datumstabellen in Power BI Desktop

**Power BI Desktop** erkennt im Hintergrund automatisch Spalten, die Datumswerte darstellen und erstellt anschließend in Ihrem Auftrag Datumshierarchien und weitere nützliche Metadaten für Ihr Modell. Diese integrierten Hierarchien können Sie benutzen, wenn Sie Berichtsfeatures wie Visuals, Tabellen, Quickmeasures und Slicer erstellen. Power BI Desktop erstellt dazu ausgeblendete Tabellen, die Sie für Ihre Berichte und DAX-Ausdrücke verwenden können.

Weitere Informationen zu diesem automatischen Verhalten finden Sie im Artikel [Automatische Angabe von Datum/Uhrzeit in Power BI Desktop](desktop-auto-date-time.md).

Viele Datenanalysten erstellen lieber eigene Datumstabellen, was selbstverständlich ebenfalls möglich ist. In **Power BI Desktop** können Sie festlegen, welche Tabelle für Ihr Modell als **Datumstabelle** verwendet werden soll. Anschließend haben Sie die Möglichkeit, datumsbezogene Visuals, Tabellen, Quickmeasures usw. zu erstellen, die auf die Daten dieser Tabelle zugreifen. Wenn Sie eine eigene Datumstabelle festlegen, können Sie die in Ihrem Modell erstellten Datumshierarchien konfigurieren und sie in **Quickmeasures** und anderen Vorgängen nutzen, die auf die Datumstabelle des Modells zurückgreifen. 

![](media/desktop-date-tables/date-tables_01.png)

## <a name="setting-your-own-date-table"></a>Festlegen einer eigenen Datumstabelle

Wählen Sie zum Festlegen einer **Datumstabelle** die Tabelle aus, die im Bereich **Fields** (Felder) als Datumstabelle verwendet werden soll. Klicken Sie anschließend mit der rechten Maustaste auf die Tabelle, und rufen Sie, wie in der folgenden Abbildung zu sehen, im angezeigten Menü **Als Datumstabelle markieren > Als Datumstabelle markieren** auf.

![](media/desktop-date-tables/date-tables_02.png)

Wie im Folgenden zu sehen ist, können Sie alternativ auch zuerst die Tabelle und anschließend über das Menüband **Modellierung** den Eintrag **Als Datumstabelle markieren** auswählen.

![](media/desktop-date-tables/date-tables_02b.png)

Wenn Sie Ihre eigene **Datumstabelle** festlegen, prüft Power BI Desktop, ob die Daten in der Spalte gültig sind. Dadurch wird sichergestellt, dass

* eindeutige Werte enthalten sind,
* keine NULL-Werte enthalten sind,
* ein zusammenhängender Bereich von Datumswerten (von Anfang bis Ende) enthalten ist
* und es sich um den Datentyp **Datum/Uhrzeit** handelt, der für jeden Wert einen identischen Zeitstempel besitzt.

Bei der Erstellung eigener Datumstabellen kommt mit großer Wahrscheinlichkeit eines der beiden Szenarios für Sie in Betracht:

* Im ersten Szenario verwenden Sie eine kanonische (standardisierte) Datumstabelle und -hierarchie. Diese Tabelle erfüllt die oben beschriebenen Prüfkriterien für eine Datumstabelle. 

* Im zweiten Szenario greifen Sie z.B. auf eine Tabelle aus Analysis Services zurück, die ein *Dim Date*-Feld enthält, das Sie als Datumstabelle nutzen möchten. 

Beim Festlegen der Datumstabelle können Sie auswählen, welche Spalte als Datumsspalte verwendet werden soll. Dazu wählen Sie im Bereich **Fields** (Felder) die Tabelle aus, klicken mit der rechten Maustaste auf sie und rufen anschließend **Als Datumstabelle markieren > Datumstabelleneinstellungen** auf. Das unten gezeigt Fenster wird geöffnet. Hier können Sie über das Dropdownmenü die Spalte auswählen, die als Datumstabelle verwendet werden soll.

![](media/desktop-date-tables/date-tables_03.png)

Beachten Sie, dass **Power BI Desktop** beim Festlegen einer eigenen Datumstabelle nicht wie sonst üblich automatisch Hierarchien erstellt und diese in Ihr Modell integriert. Wenn Sie später die Auswahl für die Datumstabelle aufheben und nicht mehr über eine manuell festgelegte Datumstabelle verfügen, erstellt Power BI Desktop die automatisch erstellten integrierten Datumstabellen für die Datumsspalten in der Tabelle erneut.

Außerdem sollten Sie beachten, dass beim Kennzeichnen einer Tabelle als Datumstabelle die integrierte (automatisch erstellte) Datumstabelle, die von Power BI Desktop erstellt wurde, entfernt wird. Dadurch funktionieren die Visuals und DAX-Elemente nicht mehr richtig, die Sie auf der Grundlage der integrierten Tabellen erstellt haben. 

## <a name="marking-your-date-table-as-the-appropriate-data-type"></a>Kennzeichnen einer Datumstabelle mit dem entsprechenden Datentyp

Wenn Sie eine eigene **Datumstabelle** festlegen, müssen Sie darauf achten, den richtige Datentyp anzugeben. Sie sollten den **Datentyp** auf **Datum/Uhrzeit** oder **Datum** festlegen. Führen Sie hierzu die folgenden Schritte aus:

1. Wählen Sie aus dem Bereich **Felder** die **Datumstabelle** aus, und erweitern Sie sie bei Bedarf. Wählen Sie anschließend die Spalte aus, die als Datum verwendet werden soll.
   
    ![](media/desktop-date-tables/date-tables_04.png) 

2. Klicken Sie auf der Registerkarte **Modellierung** auf **Datentyp:** und anschließend auf den Pfeil des Dropdownmenüs, um sich die verfügbaren Datentypen anzeigen zu lassen.

    ![](media/desktop-date-tables/date-tables_05.png)

3. Legen Sie anschließend den Datentyp für die Spalte fest. 


## <a name="next-steps"></a>Weitere Schritte

Folgende Artikel könnten Sie ebenfalls interessieren:

* [Automatische Angabe von Datum/Uhrzeit in Power BI Desktop](desktop-auto-date-time.md)
* [Datentypen in Power BI Desktop](../connect-data/desktop-data-types.md)
