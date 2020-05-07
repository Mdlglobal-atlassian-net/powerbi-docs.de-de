---
title: Connect to CSV files in Power BI Desktop (Verbinden mit CSV-Dateien in Power BI Desktop)
description: Einfaches Verbinden mit und Verwenden von CSV-Dateidaten in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c5d817af65529506a0ee515be5e287a629d6ad54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73878549"
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>Connect to CSV files in Power BI Desktop (Verbinden mit CSV-Dateien in Power BI Desktop)
Das Verbinden mit einer *CSV*-Datei (durch Trennzeichen getrennte Datei) von Power BI Desktop aus hat große Ähnlichkeit mit dem Verbinden mit einer Excel-Arbeitsmappe. Beides ist einfach, und dieser Artikel führt Sie Schritt für Schritt durch das Verbinden mit einer beliebigen CSV-Datei, auf die Sie Zugriff haben.

Wählen Sie zunächst in Power BI Desktop auf dem Menüband **Start** die Option **Daten abrufen > CSV** aus.

![](media/desktop-connect-csv/connect-to-csv_1.png)

Wählen Sie über das angezeigte Dialogfeld **Öffnen** Ihre CSV-Datei aus.

![](media/desktop-connect-csv/connect-to-csv_2.png)

Wenn Sie **Öffnen** auswählen, greift Power BI Desktop auf die Datei zu und legt bestimmte Dateiattribute fest, wie z.B. den Dateiursprung, den Trennzeichentyp und die Anzahl von Zeilen, die verwendet werden soll, um die Datentypen in der Datei zu erkennen.

Diese Dateiattribute und -optionen werden in der Dropdownauswahl oben im Dialogfeld für den **CSV-Import** angezeigt, wie nachstehend dargestellt. Sie können jede dieser erkannten Einstellungen manuell ändern, indem Sie eine andere Option aus der Dropdownliste auswählen.

![](media/desktop-connect-csv/connect-to-csv_3.png)

Wenn Sie mit der Auswahl zufrieden sind, können Sie **Laden** auswählen, um die Datei in Power BI Desktop zu importieren. Alternativ können Sie **Bearbeiten** auswählen, um den **Abfrage-Editor** zu öffnen und Ihre Daten zunächst zu strukturieren oder zu transformieren, bevor Sie sie importieren.

Nachdem Sie die Daten in Power BI Desktop geladen haben, finden Sie die Tabelle und deren Spalten (die in Power BI Desktop als Felder dargestellt werden) im Bereich **Felder** am rechten Rand der Berichtsansicht in Power BI Desktop.

![](media/desktop-connect-csv/connect-to-csv_4.png)

Das ist alles, was Sie tun müssen: Die Daten aus Ihrer CSV-Datei befinden sich nun in Power BI Desktop.

Sie können diese Daten in Power BI Desktop verwenden, um Visualisierungen oder Berichte zu erstellen und um mit anderen Daten zu interagieren, mit denen Sie möglicherweise eine Verbindung herstellen bzw. die Sie möglicherweise importieren möchten, wie z.B. Excel-Arbeitsmappen, Datenbanken oder beliebige andere Datenquellen.

> [!IMPORTANT]
> Wenn Sie eine CSV-Datei importieren, generiert Power BI Desktop *columns=x* (wobei *x* für die Anzahl der Spalten in der CSV-Datei während des anfänglichen Importvorgangs steht) als Schritt in Power Query-Editor. Wenn Sie anschließend weitere Spalten hinzufügen und die Aktualisierung der Datenquelle festgelegt ist, werden alle Spalten nach der anfänglichen *x*-Anzahl von Spalten nicht aktualisiert. 


## <a name="next-steps"></a>Weitere Schritte
Sie können mithilfe von Power BI Desktop eine Verbindung mit Daten jeglicher Art herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Datenquellen in Power BI-Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

