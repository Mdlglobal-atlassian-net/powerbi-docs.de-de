---
title: Verbinden mit einem OData-Feed in Power BI Desktop
description: Einfaches Verbinden mit und Verwenden von einem OData-Feed in Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3b95ccf558484670f8bacd8a031e94f9b0dbbddd
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Verbinden mit einem OData-Feed in Power BI Desktop
In Power BI Desktop können Sie eine Verbindung mit einem **OData-Feed** herstellen und die zugrunde liegenden Daten wie alle anderen Datenquellen in Power BI Desktop verwenden.

Wählen Sie zum Verbinden mit einem OData-Feed **Daten abrufen > OData-Feed** auf dem Menüband **Start** in Power BI Desktop aus.

![](media/desktop-connect-odata/connect-to-odata_1.png)

Tippen Sie im angezeigten Fenster **OData-Feed** Ihre OData-Feed-URL in das Dialogfeld ein, oder fügen Sie diese ein, und wählen Sie **OK** aus.

![](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop stellt eine Verbindung mit dem OData-Feed her, und zeigt die verfügbaren Tabellen und anderen Datenelementen im Fenster **Navigator** an. Wenn Sie ein Element auswählen, wird im rechten Bereich des Fensters **Navigator** eine Vorschau der Daten angezeigt. Sie können für den Import beliebig viele Tabellen auswählen. Das Fenster **Navigator** zeigt eine Vorschau der aktuell ausgewählten Tabelle an.

![](media/desktop-connect-odata/connect-to-odata_3.png)

Sie können die Schaltfläche **Bearbeiten** auswählen, wodurch der **Abfrage-Editor** gestartet wird, über den Sie die Daten aus dem OData-Feed strukturieren und transformieren können, bevor Sie sie in Power BI Desktop importieren. Alternativ können Sie die Schaltfläche **Laden** auswählen und alle Datenelemente importieren, die Sie im linken Bereich ausgewählt haben.

Wenn Sie **Laden** auswählen, importiert Power BI Desktop die ausgewählten Elemente und zeigt ein **Laden**-Fenster an, das den Importstatus darstellt.

![](media/desktop-connect-odata/connect-to-odata_4.png)

Nachdem der Vorgang abgeschlossen ist, stellt Power BI Desktop die ausgewählten Tabellen und anderen Datenelemente im Bereich **Felder** auf der rechten Seite der *Berichtsansicht* in Power BI Desktop zur Verfügung.

![](media/desktop-connect-odata/connect-to-odata_5.png)

Und das ist auch schon alles!

Sie können die von Ihrem OData-Feed importierten Daten nun in Power BI Desktop verwenden, um Visualisierungen oder Berichte zu erstellen und um mit anderen Daten zu interagieren, mit denen Sie möglicherweise eine Verbindung herstellen bzw. die Sie möglicherweise importieren möchten, wie z.B. andere Excel-Arbeitsmappen, Datenbanken oder beliebige andere Datenquellen.

### <a name="next-steps"></a>Nächste Schritte
Sie können mithilfe von Power BI Desktop eine Verbindung mit Daten jeglicher Art herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Erste Schritte mit Power BI Desktop](desktop-getting-started.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
