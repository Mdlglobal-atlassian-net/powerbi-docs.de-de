---
title: Berichtsdaten im Power BI-Berichts-Generator
description: Wenn Sie einen Bericht im Power BI Report Builder erstellen, müssen Sie zunächst die Datenquellen und Datasets erstellen, die die zugrunde liegenden Berichtsdaten darstellen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: fea4e4927b009e30bc040593f9237cc49ff73956
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921445"
---
# <a name="report-data-in-power-bi-report-builder"></a>Berichtsdaten im Power BI-Berichts-Generator

Berichtsdaten können aus mehreren Datenquellen in Ihrer Organisation stammen. Wenn Sie einen Bericht im Power BI-Berichts-Generator erstellen, müssen Sie zunächst die Datenquellen und Datasets erstellen, die die zugrunde liegenden Berichtsdaten darstellen. Jede Datenquelle enthält Informationen zur Datenverbindung. Jedes Dataset enthält einen Abfragebefehl, der die Felder festlegt, deren Daten aus einer Datenquelle verwendet werden sollen. Fügen Sie einen Datenbereich wie eine Tabelle, eine Matrix, ein Diagramm oder eine Karte hinzu, um Daten aus Datasets zu visualisieren. Wenn der Bericht verarbeitet wird, werden die Abfragen für die Datenquelle ausgeführt, und jeder Datenbereich wird nach Bedarf erweitert, sodass die Abfrageergebnisse für das Dataset dargestellt werden.  

In diesem Artikel erfahren Sie, wie Sie [eine eingebettete Datenquelle für paginierte Berichte im Power BI-Berichts-Generator erstellen](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Begriffe  
  
- **Datenverbindung:** Diese wird auch als *Datenquelle* bezeichnet. Eine Datenverbindung umfasst einen Namen und Verbindungseigenschaften, die vom Verbindungstyp abhängen. Eine Datenverbindung enthält standardmäßig keine Anmeldeinformationen. Eine Datenverbindung gibt nicht an, welche Daten von einer externen Datenquelle abgerufen werden sollen. Hierfür müssen Sie bei der Erstellung eines Datasets eine Abfrage festlegen.  
  
- **Verbindungszeichenfolge:** Eine Verbindungszeichenfolge ist eine Zeichenfolgenversion der Verbindungseigenschaften, die für die Herstellung einer Verbindung mit einer Datenquelle erforderlich sind. Die Verbindungseigenschaften hängen vom Datenverbindungstyp ab.  
  
- **Eingebettete Datenquelle:** Diese wird auch als *berichtsspezifische Datenquelle* bezeichnet. Es handelt sich um eine Datenquelle, die in einem Bericht definiert und nur von diesem verwendet wird.  
  
- **Anmeldeinformationen:** Bei Anmeldeinformationen handelt es sich um die Authentifizierungsinformationen, die angegeben werden müssen, damit der Zugriff auf externe Daten gewährt wird.  
  
##  <a name="BkMk_ReportDataTips"></a> Tipps zur Konfiguration von Berichtsdaten

 Entwerfen Sie Ihre Berichtsdatenstrategie anhand der folgenden Informationen.  
  
- **Filtern von Daten:** Berichtsdaten können in der Abfrage oder im Bericht gefiltert werden. Sie können Datasets und Abfragevariablen verwenden, um kaskadierende Parameter zu erstellen. Dadurch können Benutzer die Auswahlmöglichkeiten auf eine überschaubare Anzahl eingrenzen. Sie können Daten in einer Tabelle oder einem Diagramm je nach Parameterwerten oder anderen angegebenen Werten filtern.  
  
- **Parameter:** Abfragebefehle von Datasets, die Abfragevariablen enthalten, erstellen automatisch die entsprechenden Berichtsparameter. Sie können Parameter auch manuell erstellen. Wenn Sie einen Bericht anzeigen, werden die Parameter auf der Symbolleiste des Berichts aufgeführt. Die Benutzer können Werte auswählen, um die Berichtsdaten oder die Darstellung des Berichts zu konfigurieren. Sie können Berichtsdaten an bestimmte Zielgruppen anpassen, indem Sie Berichtsparameter mit unterschiedlichen Standardwerten erstellen, die mit derselben Berichtsdefinition verknüpft sind. Alternativ können Sie das integrierte Feld **UserID** verwenden. 
  
- **Gruppieren und Aggregieren von Daten:** Berichtsdaten können in der Abfrage oder im Bericht gruppiert und aggregiert werden. Wenn Sie Werte in der Abfrage aggregieren, können Sie weiterhin die relevanten Werte im Bericht kombinieren.  
  
- **Sortieren von Daten:** Berichtsdaten können in der Abfrage oder im Bericht sortiert werden. In Tabellen können Sie zudem eine interaktive Sortierschaltfläche hinzufügen, über die der Benutzer die Sortierreihenfolge festlegen kann.  
  
- **Ausdrucksbasierte Daten:** Da die meisten Berichtseigenschaften ausdrucksbasiert sein können und Ausdrücke Verweise auf Datasetfelder und Berichtsparameter enthalten können, können Sie leistungsstarke Ausdrücke schreiben, um die Berichtsdaten und die Darstellung zu konfigurieren. Sie können dem Benutzer ermöglichen, die angezeigten Daten über Parameter zu definieren.  
  
- **Anzeigen von Daten aus einem Dataset:** Die Daten aus einem Dataset werden in der Regel in einem oder mehreren Datenbereichen (z. B. eine Tabelle oder ein Diagramm) dargestellt.  
  
- **Anzeigen von Daten aus mehreren Datasets:** Sie können Ausdrücke in einem Datenbereich schreiben, der auf einem Dataset basiert, das Werte in einem anderen Dataset sucht oder aggregiert. Sie können Unterberichte in eine Tabelle einfügen, die auf einem Dataset basiert, um Daten aus einer anderen Datenquelle darzustellen.  
  
 Mithilfe der folgenden Liste können Sie die Datenquellen für einen Bericht definieren.  
  
- Machen Sie sich mit der Datenschichtarchitektur Ihrer Organisation für die Software und den Problemen vertraut, die möglicherweise bei bestimmten Datentypen entstehen. Machen Sie sich damit vertraut, wie Datenerweiterungen und Datenverarbeitungserweiterungen sich auf Abfrageergebnisse auswirken können. Datentypen variieren je nach Datenquelle, Datenanbieter und in der Berichtsdefinitionsdatei (RDL-Datei) gespeicherten Datentypen.  
  
- Datenquellen und Datasets werden in einem Bericht erstellt und im Power BI-Dienst veröffentlicht. Nach der Veröffentlichung können Sie die Anmeldeinformationen direkt im Power BI-Dienst oder in Ihrem Enterprise-Gateway konfigurieren. 

## <a name="next-steps"></a>Nächste Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)  
- [Leitfaden zum Datenabruf bei paginierten Berichten](../guidance/report-paginated-data-retrieval.md)
