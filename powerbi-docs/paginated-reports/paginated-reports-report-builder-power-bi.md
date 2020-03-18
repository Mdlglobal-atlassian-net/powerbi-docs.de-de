---
title: Was sind paginierte Berichte in Power BI Premium?
description: Paginierte Berichte sind seit Langem das Standardberichtsformat in SQL Server Reporting Services und stehen jetzt auch im Power BI-Dienst zur Verfügung. Diese Berichte können ausgedruckt oder freigegeben werden. Das Berichtslayout kann detailliert gesteuert werden. Sie zeigen beispielsweise alle Daten in einer Tabelle an, selbst wenn die Tabelle sich über mehrere Seiten erstreckt.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 11/27/2019
ms.openlocfilehash: 29a6e9f67258d4babc58d8195dda59afe97554c6
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79205226"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>Was sind paginierte Berichte in Power BI Premium?

Paginierte Berichte sind seit Langem das Standardberichtsformat in SQL Server Reporting Services und stehen jetzt auch im Power BI-Dienst zur Verfügung. Diese Berichte können ausgedruckt oder freigegeben werden. Sie werden als „paginiert“ bezeichnet, weil sie so formatiert sind, dass sie gut auf eine Seite passen. Sie zeigen alle Daten in einer Tabelle an, selbst wenn die Tabelle sich über mehrere Seiten erstreckt. Sie werden gelegentlich auch als „pixelperfekt“ bezeichnet, weil Sie das Berichtsseitenlayout detailliert steuern können. Paginierte Berichte basieren auf der RDL-Berichtstechnologie von SQL Server Reporting Services. Der Berichts-Generator ist das eigenständige Tool für die Erstellung paginierter Berichte. 

Paginierte Berichte können viele Seiten umfassen. Dieser Bericht umfasst beispielsweise 563 Seiten. Jede Seite ist genau strukturiert, mit einer Seite pro Rechnung und sich wiederholenden Kopf- und Fußzeilen.

Nutzen Sie das [Praxislab: Erstellen Sie einen paginierten Microsoft Power BI-Bericht](https://www.microsoft.com/handsonlabs/selfpacedlabs/details/SQ00208).

![Paginiert](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Sie können eine Vorschau Ihres Berichts im Berichts-Generator anzeigen und dann im Power BI-Dienst unter https://app.powerbi.com veröffentlichen. Sie benötigen eine Power BI Pro-Lizenz, um einen Bericht im Dienst zu veröffentlichen. Sie können paginierte Berichte unter „Mein Arbeitsbereich“ oder in anderen Arbeitsbereichen veröffentlichen und freigeben, solange sich der Arbeitsbereich in einer Power BI Premium-Kapazität befindet. Außerdem muss ein Power BI-Administrator paginierte Berichte im Abschnitt [Premium-Kapazitäten](../service-admin-premium-workloads.md#paginated-reports) des Power BI-Administratorportals aktivieren. 

## <a name="create-reports-in-power-bi-report-builder"></a>Erstellen von Berichten im Power BI-Berichts-Generator

Paginierte Berichte besitzen ihr eigenes Designtool, nämlich den Power BI-Berichts-Generator. Dabei handelt es sich um ein neues Tool mit den gleichen Grundlagen wie die zuvor verwendeten Tools zum Erstellen paginierter Berichte für Microsoft Power BI-Berichtsserver oder SQL Server Reporting Services (SSRS). Tatsächlich sind paginierte Berichte, die Sie für SSRS 2016 und 2017 oder für den Power BI-Berichtsserver lokal erstellen, mit dem Power BI-Dienst kompatibel. Der Power BI-Dienst gewährleistet Abwärtskompatibilität, sodass Sie Ihre Berichte weiterverwenden und paginierte Berichte früherer Versionen aktualisieren können. Mit Veröffentlichung sind nicht alle Berichtsfunktionen verfügbar. Unter [Einschränkungen und Überlegungen](#limitations-and-considerations) finden Sie weitere Informationen.
     
## <a name="report-from-a-variety-of-data-sources"></a>Erstellen von Berichten aus einer Vielzahl von Datenquellen

Ein einzelner paginierter Bericht kann über eine Reihe unterschiedlicher Datenquellen verfügen. Im Gegensatz zu Power BI-Berichten liegt ihm kein Datenmodell zugrunde. Für die erste Version paginierter Berichte im Power BI-Dienst erstellen Sie eingebettete Datenquellen und Datasets im Bericht selbst. Momentan können Sie keine freigegebenen Datenquellen oder freigegebene Datasets verwenden. Sie erstellen Berichte im Berichts-Generator auf dem lokalen Computer. Wenn ein Bericht eine Verbindung mit lokalen Daten herstellt, nachdem Sie den Bericht in den Power BI-Dienst hochgeladen haben, müssen Sie ein Gateway erstellen und die Datenverbindung umleiten. Hier sind die Datenquellen aufgeführt, mit denen Sie zu diesem Zeitpunkt eine Verbindung herstellen können:

- Azure SQL-Datenbank und Data Warehouse (via Basic und OAuth)
- Azure Analysis Services (über SSO)
- SQL Server über ein Gateway
- SQL Server Analysis Services über ein Gateway
- Power BI-Datasets
- Oracle
- Teradata

## <a name="design-your-report"></a>Entwerfen des Berichts  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Erstellen Sie paginierte Berichte mit Matrix-, Diagramm- und Freiformlayouts

Tabellenberichte eignen sich gut für spaltenbasierte Daten. Matrixberichte wie Kreuztabellenberichte oder PivotTable-Berichte eignen sich gut für zusammengefasste Daten. Diagrammberichte stellen Daten in einem grafischen Format dar. Freiform-*Listenberichte* können fast alles Andere wie z.B. Rechnungen darstellen. 
  
Sie können mit einem der Assistenten des Berichts-Generators starten. Die Tabellen-, Matrix- und Diagramm-Assistenten führen Sie durch die Erstellung der Verbindung mit der eingebetteten Datenquelle und dem eingebetteten Dataset. Ziehen Sie anschließend Felder per Drag & Drop, um eine Datasetabfrage zu erstellen, wählen Sie Layout und Stil aus, und passen Sie den Bericht an.  
  
Mit dem Karten-Assistenten erstellen Sie Berichte, die aggregierte Daten vor einem geografischen oder geometrischen Hintergrund anzeigen. Kartendaten können räumliche Daten aus einer Transact-SQL-Abfrage oder einer Shape-Datei des Environmental Systems Research Institute (ESRI) sein. Sie können auch einen Microsoft Bing-Kartenkachelhintergrund hinzufügen.  

### <a name="add-more-to-your-report"></a>Hinzufügen weiterer Elemente zum Bericht

Ändern Sie Ihre Daten, indem Sie sie filtern, gruppieren und sortieren bzw. Formeln oder Ausdrücke hinzufügen. Fügen Sie Diagramme, Messgeräte, Sparklines und Indikatoren hinzu, um Daten in einem visuellen Format zusammenzufassen.  Verwenden Sie Parameter und Filter, um Daten für benutzerdefinierte Sichten zu filtern. Betten Sie Bilder oder andere Ressourcen ein, oder verweisen Sie darauf – auch externe Inhalte.  

Alles in einem paginierten Bericht, vom Bericht selbst bis hin zu jedem Textfeld, jedem Bild, jeder Tabelle und jedem Diagramm, besitzt ein Array von Eigenschaften, die Sie festlegen können, damit der Bericht genau Ihren Vorstellungen entspricht.

## <a name="creating-a-report-definition"></a>Erstellen einer Berichtsdefinition

Wenn Sie einen paginierten Bericht entwerfen, erstellen Sie eigentlich eine *Berichtsdefinition*. Sie enthält keine Daten. Sie gibt an, wo die Daten bereitstehen, welche Daten abzurufen sind und wie die Daten angezeigt werden sollen. Bei Ausführung des Berichts legt der Berichtsprozessor die angegebene Berichtsdefinition zugrunde, ruft die Daten ab und kombiniert sie mit dem Berichtslayout, um den Bericht zu generieren. Sie laden die Berichtsdefinition in den Power BI-Dienst hoch (https://app.powerbi.com ), entweder in „Mein Arbeitsbereich“ oder in einen Arbeitsbereich, den Sie gemeinsam mit Ihren Kollegen verwenden. Ist die Berichtsdatenquelle lokal gespeichert, leiten Sie die Datenquellenverbindung nach dem Hochladen des Berichts so um, dass sie über ein Gateway verläuft. 

## <a name="view-your-paginated-report"></a>Anzeigen Ihres paginierten Berichts
Sie können Ihren paginierten Bericht im Power BI-Dienst in einem Browser und auch in den Power BI Mobile-Apps anzeigen. Sie können den Bericht über den Power BI-Dienst in mehrere Formate exportieren, darunter HTML, MHTML, PDF, XML, CSV, TIFF, Word und Excel. Zudem können Sie ihn für andere Benutzer freigeben.  

## <a name="create-a-subscription-to-your-report"></a>Erstellen eines Abonnements für Ihren Bericht

Sie können jetzt im Power BI-Dienst E-Mail-Abonnements für paginierte Berichte für sich selbst und andere einrichten. Im Allgemeinen ist dieser Vorgang mit dem Abonnieren von Berichten und Dashboards im Power BI-Dienst identisch. Durch das Einrichten von Abonnements können Sie entscheiden, ob Sie die E-Mails täglich, wöchentlich oder stündlich erhalten möchten. Das Abonnement enthält eine PDF-Anlage mit der gesamten Berichtsausgabe.

Weitere Details finden Sie im Artikel [Subscribe yourself and others to paginated reports in the Power BI service (Abonnieren von paginierten Berichten im Power BI-Dienst für sich selbst und andere)](../consumer/paginated-reports-subscriptions.md). 

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Hier sind einige andere Features aufgeführt, die in der ersten Version nicht unterstützt werden:

- Anheften von Berichtsseiten oder Visuals an Power BI-Dashboards. Sie können noch immer Visualisierungen aus einem lokalen paginierten Bericht auf einem Power BI-Berichtsserver oder einem Reporting Services-Berichtsserver an ein Power BI-Dashboard anheften. Weitere Informationen finden Sie unter [Anheften von Reporting Services-Elementen an Power BI-Dashboards](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards).
- Dokumentstruktur.
- Unterberichte und Drillthroughberichte.  Sie können jedoch auch URL-Parameter mit paginierten Berichten verwenden, um Drillthroughszenarios zu erreichen.
- Freigegebene Datenquellen und freigegebene Datasets.

 
## <a name="next-steps"></a>Nächste Schritte

- [Installieren des Power BI-Berichts-Generators aus dem Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Erstellen eines paginierten Berichts](paginated-reports-quickstart-aw.md)
- [Enter data directly in a paginated report (Eingeben von Daten direkt in einem paginierten Bericht)](paginated-reports-enter-data.md)
- [Praxislab: Erstellen Sie einen paginierten Microsoft Power BI-Bericht](https://www.microsoft.com/handsonlabs/selfpacedlabs/details/SQ00208)
- [Tutorial: Einbetten paginierter Power BI-Berichte in eine Anwendung für Kunden](../developer/embed-paginated-reports-customers.md).