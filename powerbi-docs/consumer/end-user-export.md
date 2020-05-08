---
title: Exportieren von Daten aus einem Power BI-Visual
description: Exportieren Sie Daten aus einem Berichts- und Dashboardvisual, und zeigen Sie sie in Excel an.
author: mihart
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 811eaa9769a099122597d7132de80cbc2d22a51b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79040139"
---
# <a name="export-data-from-a-visual"></a>Exportieren von Daten aus einer Visualisierung

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Wenn Sie die Daten anzeigen möchten, auf deren Grundlage ein Visual erstellt wurde, können Sie die [Daten in Power BI anzeigen](end-user-show-data.md) oder in Excel exportieren. Die Option zum Exportieren der Daten erfordert einen bestimmten Typ oder eine bestimmte Lizenz und Bearbeitungsberechtigungen für den Inhalt. Wenn Sie nicht exportieren können, wenden Sie sich an den Power BI-Administrator. Zum Exportieren von Daten ist eine Power BI Pro-Lizenz erforderlich, entweder eine Pro-Benutzerlizenz oder eine Pro-Benutzerlizenz innerhalb einer Organisation mit Lizenz für Premium-Kapazität. In der Regel wird dieser Lizenztyp von *Berichtsdesignern* und nicht von *Consumern* verwendet. Weitere Informationen finden Sie unter [Welche Lizenz habe ich?](end-user-license.md).


## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Aus einem Visual in einem Power BI-Dashboard

1. Starten Sie ein Power BI-Dashboard. Hier verwenden wir das Dashboard aus der ***Beispiel für Vertrieb und Marketing***-App. Sie können [diese APP von AppSource.com herunterladen](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282).

    ![App-Dashboard](media/end-user-export/power-bi-dashboards.png)

2. Zeigen Sie auf ein Visual, um **Weitere Optionen** (...) anzuzeigen, und klicken Sie, um das Aktionsmenü anzuzeigen.

    ![Bei Auswahl der Auslassungspunkte angezeigtes Menü](media/end-user-export/power-bi-options-menu.png)

3. Wählen Sie **In CSV exportieren** aus.

4. Was als Nächstes passiert, hängt davon ab, welchen Browser Sie verwenden. Möglicherweise werden Sie aufgefordert, die Datei zu speichern, oder es wird ein Link zur exportierten Datei am unteren Rand des Browsers angezeigt. 

    ![Chrome-Browser mit Link zu exportierter Datei](media/end-user-export/power-bi-dashboard-exports.png)

5. Öffnen Sie die Datei in Excel. 

    > [!NOTE]
    > Wenn Sie keine Berechtigungen für die Daten haben, können Sie nicht nach Excel exportieren oder in Excel öffnen.  

    ![„Total Units YTD“ (Gesamte Einheiten seit Jahresbeginn) in Excel](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>Aus einem Visual in einem Bericht
Sie können Daten aus einem Visual in einem Bericht im CSV- oder XLSX-Format (Excel) exportieren. 

1. Wählen Sie auf einem Dashboard eine Kachel aus, um den zugrunde liegenden Bericht zu öffnen.  In diesem Beispiel wählen wir das gleiche Visual wie oben aus, *Total Units YTD Var %* (Gesamte Einheiten seit Jahresbeginn – Abweichung in %). 

    ![Hervorgehobene Dashboardkachel](media/end-user-export/power-bi-export-reports.png)

    Diese Kachel wurde aus dem Bericht des *Beispiels für Vertrieb und Marketing* erstellt, das ist der Bericht, der geöffnet wird. Er wird mit der Seite geöffnet, die das ausgewählte Kachelvisual enthält. 

2. Wählen Sie das Visual im Bericht aus. Beachten Sie den Bereich **Filter** auf der rechten Seite. Für dieses Visual werden Filter angewendet. Weitere Informationen zu Filtern finden Sie unter [Verwenden von Filtern in einem Bericht](end-user-report-filter.md).

    ![Ausgewählter Bereich „Filter“](media/end-user-export/power-bi-export-filter.png)


3. Klicken Sie rechts oben im Visual auf **Weitere Optionen (...)** . Wählen Sie **Daten exportieren** aus.

    ![Exportieren ausgewählter Daten aus der Dropdownliste](media/end-user-export/power-bi-export-report.png)

4. Sie sehen Optionen zum Exportieren zusammengefasster oder zugrunde liegender Daten. Wenn Sie die *Beispiel für Vertrieb und Marketing*-App verwenden, werden die **Zugrunde liegenden Daten** deaktiviert. Es können jedoch auch Berichte angezeigt werden, bei denen beide Optionen aktiviert sind. Im Folgenden wird der Unterschied erläutert.

    **Zusammengefasste Daten**: Wählen Sie diese Option aus, wenn Sie Daten für das exportieren möchten, was aktuell im Visual angezeigt wird.  Diese Exportart zeigt nur die Daten an, die zum Erstellen des Visuals verwendet wurden. Wenn für das Visual Filter verwendet werden, werden die Daten, die Sie exportieren, ebenfalls gefiltert. Beispielsweise enthält der Export für dieses Visual nur Daten für 2014 und die zentrale Region sowie nur Daten für vier Hersteller: VanArsdel, Natura, Aliqui und Pirum. Wenn das Visual über Aggregate (Summe, Durchschnitt usw.) verfügt, wird der Export ebenfalls aggregiert. 
  

    **Zugrunde liegende Daten**: Wählen Sie diese Option aus, wenn Sie Daten für das exportieren möchten, was Sie im Visual sehen, **plus** zusätzlicher Daten aus dem zugrunde liegenden Dataset.  Dies kann Daten umfassen, die im Dataset enthalten sind, aber nicht im Visual verwendet werden. Wenn für das Visual Filter verwendet werden, werden die Daten, die Sie exportieren, ebenfalls gefiltert.  Wenn das Visual über Aggregate (Summe, Durchschnitt usw.) verfügt, wird die Aggregation durch den Export entfernt. Die Daten werden im Wesentlichen vereinfacht. 

    ![Menü zur Auswahl von zugrunde liegenden oder zusammengefassten Daten](media/end-user-export/power-bi-export-underlying.png)

5. Was als Nächstes passiert, hängt davon ab, welchen Browser Sie verwenden. Möglicherweise werden Sie aufgefordert, die Datei zu speichern, oder es wird ein Link zur exportierten Datei am unteren Rand des Browsers angezeigt. 

    ![Anzeige der exportierten Datei im Microsoft Edge-Browser](media/end-user-export/power-bi-export-edge-browser.png)

    > [!NOTE]
    > Wenn Sie keine Berechtigungen für die Daten haben, können Sie nicht nach Excel exportieren oder in Excel öffnen.  


6. Öffnen Sie die Datei in Excel. Vergleichen Sie die Menge der exportierten Daten mit den Daten, die wir aus dem gleichen Visual auf dem Dashboard exportiert haben. Der Unterschied besteht darin, dass dieser Export **zugrunde liegende Daten** enthält. 

    ![Beispiel für Excel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Nächste Schritte

[Anzeigen der zum Erstellen einer Visualisierung verwendeten Daten](end-user-show-data.md)