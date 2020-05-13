---
title: Datenkategorisierung in Power BI Desktop
description: Datenkategorisierung in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4ce9946672514d3d3f181c573789b256888a4372
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83325849"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Festlegen von Datenkategorien in Power BI Desktop
In Power BI Desktop können Sie die *Kategorie der Daten* für eine Spalte angeben, damit Power BI Desktop weiß, wie es die entsprechenden Werte in einer Visualisierung behandeln soll.

Beim Importieren von Daten in Power BI Desktop, können andere Informationen als die Daten selbst abgerufen werden, z. B. die Tabellen- und Spaltennamen, und ob es sich bei den Daten um einen Primärschlüssel handelt. Diese Informationen nutzt Power BI Desktop, um einige Annahmen darüber aufzustellen, welche Standardbedingungen bei der Erstellung einer Visualisierung für Sie von Vorteil sein könnten.
Hier ein Beispiel: Wenn eine Spalte numerische Werte enthält, die Sie wahrscheinlich auf irgendeine Weise aggregieren möchten, wird diese in Power BI Desktop im Bereich **Visualisierungen** im Bereich **Werte** platziert. Oder bei einer Spalte mit Datums- und Uhrzeitwerten geht Power BI Desktop davon aus, dass Sie diese wahrscheinlich als Zeit-Hierarchie-Achse verwenden.

Es gibt jedoch einige Fälle, die etwas komplizierter sind, wie z. B. Geografie. Betrachten Sie die folgende Tabelle aus einem Excel-Arbeitsblatt:

![](media/desktop-data-categorization/datacategorizationtable.png)

Soll Power BI Desktop die Codes in der Spalte **GeoCode** als Abkürzung für ein Land oder einen US-Bundesstaat behandeln?  Dies ist nicht klar, da ein solcher Code beides bedeuten kann. Beispielsweise kann AL Alabama oder Albanien bedeuten, AR kann Arkansas oder Argentinien bedeuten, oder CA kann Kalifornien oder Kanada bedeuten. Dies macht einen Unterschied, wenn das Feld „GeoCode“ auf einer Karte dargestellt werden soll. 

Soll in Power BI Desktop eine Weltkarte mit hervorgehobenen Ländern angezeigt werden? Oder soll ein Bild der Vereinigten Staaten mit hervorgehobenen Bundesstaaten angezeigt werden?  Für solche Daten können Sie eine Datenkategorie angeben. Durch die Kategorisierung von Daten werden die Informationen, die Power BI-Desktop zur Bereitstellung der besten Visualisierung verwenden kann, noch weiter verfeinert.  

**Angeben einer Datenkategorie**

1. In der Ansicht **Bericht** oder der Ansicht **Daten** wählen Sie in der Liste **Felder** das Feld aus, das nach einer anderen Kategorisierung sortiert werden soll.
2. Klicken Sie in der Leiste auf der Registerkarte **Modellierung** im Bereich **Eigenschaften** auf den Dropdownpfeil neben **Datenkategorie**.  Daraufhin wird eine Liste der Datenkategorien angezeigt, die Sie für die Spalte auswählen können. Möglicherweise sind einige Optionen deaktiviert, wenn sie mit dem aktuellen Datentyp der Spalte nicht funktionieren.  Wenn eine Spalte beispielsweise den Typ Datum oder Uhrzeit aufweist, erlaubt Power BI Desktop Ihnen nicht das Auswählen geografischer Datenkategorien. 
3. Wählen Sie die gewünschte Kategorie aus.

   ![](media/desktop-data-categorization/desktop-data-categorization.png)

Möglicherweise möchten Sie auch das [geografische Filtern für mobile Power BI-Apps](desktop-mobile-geofiltering.md) kennenlernen.

