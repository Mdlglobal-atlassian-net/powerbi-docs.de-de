---
title: Herstellen einer Verbindung mit einer Google BigQuery-Datenbank in Power BI Desktop
description: Einfaches Verbinden mit und Verwenden von Google BigQuery in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b88be05c1e3890dd8ac63503d9279f51b1d9eec9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73876503"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Herstellen einer Verbindung mit einer Google BigQuery-Datenbank in Power BI Desktop
In Power BI Desktop können Sie eine Verbindung mit einer **BigQuery**-Datenbank herstellen und die zugrunde liegenden Daten wie alle anderen Datenquellen in Power BI Desktop verwenden.

## <a name="connect-to-google-bigquery"></a>Herstellen einer Verbindung mit Google BigQuery
Wählen Sie in Power BI Desktop im Menüband **Start** die Option **Daten abrufen** aus, um eine Verbindung mit einer **BigQuery**-Datenbank herzustellen. Wählen Sie in den Kategorien auf der linken Seite **Datenbank** aus. Anschließend wird **Google BigQuery** angezeigt.

![Dialogfeld „Daten abrufen“ für Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

Melden Sie sich im Fenster **Google BigQuery**, das angezeigt wird, bei Ihrem Google BigQuery-Konto an, und wählen Sie **Verbinden** aus.

![Anmelden bei Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

Wenn Sie sich angemeldet habe, sehen Sie das folgende Fenster, das angibt, dass Sie authentifiziert wurden. 

![Bei Google angemeldet](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Nachdem die Verbindung erfolgreich hergestellt wurde, wird das Fenster **Navigator** mit den auf dem Server verfügbaren Daten angezeigt. Aus diesen können Sie ein oder mehrere Elemente auswählen, die importiert und in **Power BI Desktop** verwendet werden sollen.

![Daten von Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
Beim **BigQuery**-Connector sind einige Einschränkungen und Überlegungen zu beachten:

* Der Google BigQuery-Connector ist in Power BI Desktop und im Power BI-Dienst verfügbar. Im Power BI-Dienst kann über die Cloud-zu-Cloud-Verbindung von Power BI auf Google BigQuery zugegriffen werden.

Sie können Power BI mit dem **Abrechnungsprojekt** von Google BigQuery verwenden. Power BI verwendet standardmäßig das erste Projekt aus der Liste, die für den Benutzer zurückgegeben wird. Um das Verhalten des Abrechnungsprojekts anzupassen, wenn dieses mit Power BI verwendet wird, gehen Sie folgendermaßen vor:

 * Geben Sie folgende Option im zugrunde liegenden Quellschritt an, der mithilfe des **Power Query-Editors** in Power BI Desktop angepasst werden kann:

    ```Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])```

## <a name="next-steps"></a>Weitere Schritte
Sie können mithilfe von Power BI Desktop eine Verbindung mit Daten jeglicher Art herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Datenquellen in Power BI-Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

