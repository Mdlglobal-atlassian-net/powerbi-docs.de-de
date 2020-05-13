---
title: Analysis Services – Mehrdimensionale Daten in Power BI Desktop
description: 'SQL Server Analysis Services (SSAS): mehrdimensionale Daten in Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83287692"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Herstellen einer Verbindung zu mehrdimensionalen SSAS-Modellen in Power BI Desktop

Mit Power BI Desktop können Sie auf *mehrdimensionale SSAS-Modelle*(häufig als *SSAS MD* bezeichnet) zugreifen.

Wenn Sie eine Verbindung mit einer SSAS MD-Datenbank herstellen möchten, wählen Sie **Daten abrufen** aus, und klicken Sie erst auf **Datenbank** > **SQL Server Analysis Services-Datenbank** und anschließend auf **Verbinden**:

![SSAS-Datenbank, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Sowohl der Power BI-Dienst als auch Power BI Desktop unterstützen mehrdimensionale SSAS-Modelle im Liveverbindungsmodus. Sie können Berichte mit Verwendung von **mehrdimensionalen SSAS-Modellen** auch im Livemodus im Power BI-Dienst veröffentlichen oder in den Dienst hochladen.

## <a name="capabilities-and-features-of-ssas-md"></a>Features und Funktionen von SSAS MD

In den folgenden Abschnitten werden die Features und Funktionen von Power BI- und SSAS MD-Verbindungen beschrieben.

### <a name="tabular-metadata-of-multidimensional-models"></a>Tabellarische Metadaten von mehrdimensionalen Modellen

Die folgende Tabelle beschreibt die Beziehungen zwischen mehrdimensionalen Objekten und den tabellarischen Metadaten, die an Power BI Desktop zurückgegeben werden. Power BI fragt das Modell nach tabellarischen Metadaten ab. Basierend auf den zurückgegebenen Metadaten führt Power BI Desktop entsprechende DAX-Abfragen für SSAS aus, wenn Sie eine Visualisierung erstellen (z. B. eine Tabelle, eine Matrix, ein Diagramm oder einen Slicer).

| Mehrdimensionales BISM-Objekt | Tabellarische Metadaten |
| --- | --- |
| Cube |Modell |
| Cubedimension |Tabelle |
| Dimensionsattribute (Schlüssel), Name |Spalten |
| Measuregruppe |Tabelle |
| Measure |Measure |
| Measures ohne zugeordnete Measuregruppe |Innerhalb einer Tabelle mit dem Namen *Measures* |
| Beziehung Cubedimension -> Measuregruppe |Beziehung |
| Perspektive |Perspektive |
| KPI |KPI |
| Benutzerhierarchien/Hierarchien aus über- und untergeordneten Elementen |Hierarchien |

### <a name="measures-measure-groups-and-kpis"></a>Measures, Measuregruppen und KPIs

Measuregruppen in einem mehrdimensionalen Cube werden im Bereich **Felder** als Tabellen mit einem Sigma ∑ verfügbar gemacht. Berechnete Measures, die nicht über eine zugeordnete Measuregruppe verfügen, werden in den tabellarischen Metadaten in einer speziellen Tabelle namens *Measures* gruppiert.

Zur Vereinfachung von komplexen Modellen können Sie in einem mehrdimensionalen Modell festlegen, dass mehrere Measures oder KPIs in einem Cube im Ordner *Anzeigeordner* gespeichert werden. Power BI erkennt Anzeigeordner in tabellarischen Metadaten und zeigt Measures und KPIs in den Anzeigeordnern an. KPIs in mehrdimensionalen Datenbanken unterstützen *Wert*, *Ziel*, *Statusgrafik* und *Trendgrafik*.

### <a name="dimension-attribute-type"></a>Dimensionsattributtyp

Mehrdimensionale Modelle unterstützen auch das Zuordnen von Dimensionsattributen zu bestimmten Dimensionsattributtypen. Beispielsweise wird eine Dimension **Geografie**, bei der den Dimensionsattributen *Ort*, *Bundesland/Kanton*, *Land* und *Postleitzahl* die entsprechenden Geografietypen zugeordnet sind, in den tabellarischen Metadaten verfügbar gemacht. Power BI erkennt die Metadaten und ermöglicht es Ihnen dadurch, Kartenvisualisierungen zu erstellen. Damit Sie solche Zuordnungen schnell erkennen können, wird in Power BI im Bereich *Feld* neben dem betreffenden Element ein **Kartensymbol** angezeigt.

Power BI kann auch Bilder rendern, wenn Sie ein Feld mit den URLs (Uniform Resource Locator) der Bilder angeben. Sie können diese Felder als *ImageURL*-Typen in SQL Server Data Tools (oder anschließend in Power BI) angeben. Die Typinformationen werden dann für Power BI in den tabellarischen Metadaten bereitgestellt. Power BI kann dann diese Bilder aus der URL abrufen und in Visuals anzeigen.

### <a name="parent-child-hierarchies"></a>Hierarchien aus über- und untergeordneten Elementen

Mehrdimensionale Modelle unterstützen Hierarchien aus über- und untergeordneten Elementen (Über-/Unterordnungshierarchien). Diese werden in den tabellarischen Metadaten als *Hierarchie* dargestellt. Jede Ebene in einer Über-/Unterordnungshierarchie wird als ausgeblendete Spalte in den tabellarischen Metadaten verfügbar gemacht. Das Schlüsselattribut der über- und untergeordneten Dimension wird in den tabellarischen Metadaten nicht verfügbar gemacht.

### <a name="dimension-calculated-members"></a>Berechnete Dimensionselemente

Mehrdimensionale Modelle unterstützen das Erstellen verschiedener Arten von *berechneten Elementen*. Die beiden häufigsten Arten von berechneten Elementen sind:

* berechnete Elemente in Attributhierarchien, die nicht *allen* Elementen gleichgeordnet sind
* Berechnete Elemente in Benutzerhierarchien

Mehrdimensionale Modelle machen *berechnete Elemente in Attributhierarchien* als Werte in einer Spalte verfügbar. Beim Verfügbarmachen dieser Art von berechneten Elementen gibt es einige zusätzliche Optionen und Einschränkungen:

* Ein Dimensionsattribut kann ein optionales *UnknownMember*-Element aufweisen.

* Ein Attribut, das berechnete Elemente enthält, kann nicht das Schlüsselattribut der Dimension sein, es sei denn, es ist das einzige Attribut der Dimension.

* Ein Attribut, das berechnete Elemente enthält, kann kein über- bzw. untergeordnetes Attribut sein.

Die berechneten Elemente von Benutzerhierarchien werden nicht in Power BI verfügbar gemacht. Stattdessen können Sie eine Verbindung mit einem Cube herstellen, der berechnete Elemente in Benutzerhierarchien enthält. Ihnen werden allerdings keine berechneten Elemente angezeigt, wenn diese nicht den oben aufgeführten Einschränkungen entsprechen.

### <a name="security"></a>Sicherheit

Mehrdimensionale Modelle unterstützen die Sicherheit auf Dimensions- und Zellenebene mithilfe von *Rollen*. Wenn Sie einen Cube mit Power BI verbinden, werden Sie authentifiziert, und es wird geprüft, ob Sie über die benötigten Berechtigungen verfügen. Wenn für einen Benutzer *Dimensionssicherheit* festgelegt wurde, sind die entsprechenden Dimensionselemente für den Benutzer in Power BI nicht sichtbar. Wenn für einen Benutzer jedoch eine Berechtigung mit *Zellensicherheit* definiert wurde, bei der Einschränkungen für bestimmte Zellen bestehen, kann dieser Benutzer über Power BI keine Verbindung mit dem Cube herstellen.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Die Verwendung von SSAS MD unterliegt bestimmten Einschränkungen:

* Nur die Enterprise-und BI-Editionen von SQL Server 2014 unterstützen Liveverbindungen. Bei der Standardedition von SQL Server ist SQL Server 2016 oder höher für Liveverbindungen erforderlich.

* *Aktionen* und *benannte Mengen* werden nicht für Power BI verfügbar gemacht. Dennoch können Sie eine Verbindung mit mehrdimensionalen Cubes herstellen, die auch Aktionen oder benannte Mengen enthalten, um entsprechende Visuals und Berichte zu erstellen.

* Wenn Power BI Metadaten für ein SSAS-Modell anzeigt, können Sie gelegentlich keine Daten aus dem Modell abrufen. Dies kann passieren, wenn Sie die 32-Bit-Version des MSOLAP-Anbieters installiert haben, jedoch nicht die 64-Bit-Version. Die Installation der 64-Bit-Version kann dieses Problem beheben.

* Sie können keine Measures auf *Berichtsebene* erstellen, wenn Sie einen Bericht erstellen, der über eine Liveverbindung mit einem mehrdimensionalen SSAS-Modell verbunden ist. Es stehen nur die im MD-Modell definierte Measures zur Verfügung.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Unterstützte Features von SSAS MD in Power BI Desktop

Der Verbrauch der folgenden Elemente wird in dieser Version von SSAS MD unterstützt. Weitere Informationen finden Sie unter [Grundlegendes zu Power View für mehrdimensionale Modelle](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014).

* Standardelemente
* Dimensionsattribute
* Typen von Dimensionsattributen
* Berechnete Dimensionselemente, die
  * einzelne reale Elemente sein müssen, wenn die Dimension über mehrere Attribute verfügt
  * nur Schlüsselattribute der Dimension sein können, wenn es sich um das einzige Attribut handelt
  * keine über- bzw. untergeordneten Attribute sein dürfen
* Dimensionssicherheit
* Anzeigeordner
* Hierarchien
* ImageUrls
* KPIs
* KPI-Trends
* Measures (mit oder ohne Measuregruppen)
* Measures als Varianten

## <a name="troubleshooting"></a>Problembehandlung

In der folgenden Liste sind alle bekannten Probleme beim Verbinden mit SQL Server Analysis Services (SSAS) aufgeführt.

* **Fehler: Das Modellschema konnte nicht geladen werden**: Dieser Fehler tritt normalerweise nur dann auf, wenn der Benutzer, der versucht, eine Verbindung mit Analysis Services herzustellen, keine Zugriffsberechtigungen für die Datenbank bzw. den Cube besitzt.
