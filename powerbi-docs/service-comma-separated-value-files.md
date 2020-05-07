---
title: Abrufen von Daten aus kommagetrennten Dateien (CSV)
description: Erfahren Sie, wie Sie Daten von CSV-Dateien in Power BI aufrufen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: a33c8a45f4f32efb0a47df82b8af23d42c281ae9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73855528"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Abrufen von Daten aus kommagetrennten Dateien (CSV)
![](media/service-comma-separated-value-files/csv_icon.png)

Kommagetrennte Dateien, häufig als CSV bezeichnet, sind einfache Textdateien mit Datenzeilen, in denen jeder Wert durch ein Komma getrennt ist. Diese Dateitypen können große Mengen an Daten bei einer relativ geringen Dateigröße enthalten; damit sind sie als Datenquelle für Power BI ideal geeignet. Sie können eine Beispiel-CSV-Datei [hier](https://go.microsoft.com/fwlink/?LinkID=619356) herunterladen.

Falls Sie eine CSV-Datei haben, ist es an der Zeit, sie in Ihre Power BI-Website als Dataset zu übertragen. Dort können Sie Ihre Daten durchsuchen, Dashboards erstellen, und Ihre Einblicke mit anderen teilen.

>[!TIP]
>Viele Organisationen geben jeden Tag eine CSV-Datei mit aktualisierten Daten aus. Damit Ihr Dataset in Power BI mit der aktualisierten Datei synchron bleibt, stellen Sie sicher, dass die Datei auf OneDrive mit dem gleichen Namen gespeichert wird.

## <a name="where-your-file-is-saved-makes-a-difference"></a>Der Speicherort Ihrer Datei ist entscheidend
**Lokal** – Falls Sie Ihre CSV-Datei auf einem lokalen Laufwerk auf Ihrem Computer oder an einem anderen Speicherort in Ihrer Organisation speichern, können Sie über Power BI Ihre Datei in Power BI *importieren*. In Wahrheit verbleibt Ihre Datei aber auf Ihrem lokalen Laufwerk. Die Datei wird also eigentlich gar nicht in Power BI importiert. Tatsächlich wird ein neues Dataset in Power BI erstellt, und die Daten aus der CSV-Datei werden in das Dataset geladen.

**OneDrive - Business** – Falls Sie OneDrive for Business haben und Sie sich mit dem gleichen Konto dort anmelden wie bei Power BI, ist dies der bei weitem effektivste Weg, Ihre CSV-Datei und Ihr Dataset, Berichte und Dashboards mit Power BI synchron zu halten. Da sich sowohl Power BI als auch OneDrive in der Cloud befinden, *verbindet* sich Power BI etwa einmal in der Stunde mit Ihrer Datei in OneDrive. Wenn Änderungen gefunden werden, werden Ihre Dataset, Berichte und Dashboards in Power BI automatisch aktualisiert.

**OneDrive – Persönlich** – Wenn Sie Ihre Dateien in Ihrem eigenen OneDrive-Konto speichern, erhalten Sie dennoch viele der Vorteile, die Ihnen OneDrive for Business bieten würde. Der Hauptunterschied besteht darin, dass Sie sich beim ersten Verknüpfen mit Ihrer Datei, mit Ihrem Microsoft-Konto bei OneDrive anmelden müssen (mit „Daten abrufen“ > „Dateien“ > „OneDrive – Persönlich“). Normalerweise sind Ihr Microsoft- und Ihr Power BI-Konto nicht identisch. Wählen Sie die Option „Angemeldet bleiben“ aus, wenn Sie sich mit Ihrem Microsoft-Konto bei OneDrive anmelden. Auf diese Weise ist Power BI in der Lage, sich etwa einmal die Stunde mit Ihrer Datei zu verbinden und sicherzustellen, dass Ihr Dataset in Power BI synchronisiert ist.

**SharePoint-Teamwebsites** – Ihre Power BI Desktop-Dateien in SharePoint-Teamwebsites zu speichern funktioniert ähnlich wie das Speichern in OneDrive for Business. Der größte Unterschied besteht im Herstellen der Verknüpfung zur Datei aus Power BI. Sie können eine URL angeben oder eine Verknüpfung mit einem Stammordner erstellen.

## <a name="import-or-connect-to-a-csv-file"></a>Importieren von oder Herstellen einer Verbindung mit einer CSV-Datei
>[!IMPORTANT]
>Die maximale Dateigröße für Importe in Power BI beträgt 1 GB.

1. Klicken Sie im Navigatorbereich von Power BI auf **Daten abrufen**.
   
   ![](media/service-comma-separated-value-files/csv_get_data_button.png)
2. Klicken Sie in **Dateien** auf **Abrufen**.
   
   ![](media/service-comma-separated-value-files/csv_files_get.png)
3. Suchen Sie Ihre Datei.
   
   ![](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>Nächste Schritte
**Durchsuchen Sie Ihre Daten** – Wenn Ihnen Ihre Daten aus der Datei in Power BI zur Verfügung stehen, ist es an der Zeit, diese zu durchsuchen. Klicken Sie einfach mit der rechten Maustaste auf das neue Dataset, und klicken Sie dann auf **Durchsuchen**.

**Zeitplanaktualisierung** – Falls Ihre Datei auf einem lokalen Laufwerk gespeichert ist, können Sie die geplante Aktualisierung einrichten, damit Ihr Dataset und Ihre Berichte in Power BI auf dem neuesten Stand bleiben. Weitere Informationen finden Sie unter [Aktualisieren von Daten in Power BI](refresh-data.md). Falls Ihre Datei auf OneDrive gespeichert wird, synchronisiert sich Power BI automatisch etwa jede Stunde mit ihr.

